//Initial study DATA
var gArrayPOSratioEMST = newArray(1.0125,1.0208,1.1334,1.1745,1.0855,1.006,1.0203,1.0682,1.0831,1.0217,1.2387,1.0008,1.0274,1.0232,1.01,1.0789,1.0188,1.0111,1.1549,1.0031,1.0371,1.1358,1.0179,1.0457,1.0489,1.3193,1.061,1.0421,1.0876,1.0288,1.0069,1.0536,1.1276,1.4015,1.3676,1.0991,1.2825,1.0202,1.2451,1.1729,1.0637,1.003,1.18,1.2501,1.0579,1.102,1.054,1.0926,1.0189,1.0325);
var gArrayPOSCV = newArray(25.2318,28.5887,33.9371,32.5735,33.4155,23.7978,26.6098,28.8937,30.1027,25.0326,31.774,21.975,28.4697,27.3007,28.2409,29.2797,26.7337,17.278,23.8023,24.2177,29.6064,31.7281,23.5547,27.4556,28.8994,29.8789,30.4936,24.2454,29.3424,23.6906,26.4045,31.2737,36.0426,27.5682,30.8021,28.4321,34.7514,28.3104,31.8804,33.8804,28.248,26.4925,29.8255,27.3456,29.3066,31.1633,26.9928,26.4849,25.7135,26.2954);
var gArrayNEGratioEMST = newArray(1.6349,4.026,2.4982,1.4459,1.6675,2.0649,1.3689,2.0101,1.5169,1.9913,1.5306,1.8978,1.8189,1.0773,1.7934,1.6518,1.777,1.2283,2.3131,2.5092,12.4268,2.1691,1.3048,2.3763,1.1497,1.1427,3.4538,1.6826,1.8034,1.3047,1.1592,1.5398,1.9414,1.1275,1.9423,2.3564,1.297,1.4236,1.7038,7.5308,1.1174,2.8472,1.647,5.4936,4.1207,1.433,1.8929,2.046,1.1743,1.6223,2.5644,1.573,1.7215,1.5179,2.0337,2.1316,3.6529,1.3978,1.0765,2.467,4.3789,1.2628,2.324);
var gArrayNEGCV = newArray(35.5008,59.3988,46.9394,37.3711,34.2528,40.6022,36.4797,40.5854,38.1477,30.7055,34.1906,45.8811,45.0497,29.406,49.0778,44.6837,38.3721,37.3124,42.1968,39.6026,46.1495,41.9484,39.488,46.475,35.6924,32.0829,49.5905,38.8522,39.3631,35.9175,37.4294,45.6175,53.1883,32.6717,43.8761,39.4573,35.4207,31.5192,39.1264,63.0457,32.0064,45.4443,33.6276,68.7504,45.8436,35.796,41.4606,33.4245,34.7777,42.6274,39.4284,40.2255,36.3449,32.7774,36.8413,44.5004,52.2497,38.9334,29.5311,52.1478,50.0638,33.4608,37.8251);

var gEntropy_minimum_intensity_value = 100;
var gMINIMUM_HEMATOX=0.12; //IOD value minimum hematox accepted value for a nucleus to be considered true
var gCount = newArray(50);
var gDirParameters;
var gDirStackTemp;
var gNumberInStack;
var gStackName;
var gDAB = "DAB_INTENSITY_OF_SAMPLE";
var gHEMA = "HEMA_INTENSITY_OF_SAMPLE";
var g_MatrixSamplingCounter = 1; // determines size of matrix sampling 1 -> 3x3; 2 -> 5x5; 3 -> 7x7 etc.
var g_iSizeMatrixSampling; // 3x3 -> 9 determined ast the beginning of the macro
var g_iTotalNuclei=0;
var g_Sum_Edge_distance_all_points=0;
var g_Sum_Edge_distance_pos_points=0;
var g_Number_Edge_all_points=0;
var g_Number_Edge_pos_points=0;

//Unit vectors values matching original HemaHarris_DAB_CCI
var gR1default = 0.330927;
var gG1default = 0.56322366;
var gB1default = 0.7571436;
var gR2default = 0.6614027;
var gG2default = 0.63092554;
var gB2default = 0.4055607;
var gR3default = 0.0084599;
var gG3default = 0.96940845;
var gB3default = 0.24530739;

var gR1;
var gG1;
var gB1;
var gR2;
var gG2;
var gB2;
var gR3;
var gG3;
var gB3;

var gUnitVectorsStatus;

//Values for logistic funtion

var gInterceptdefault = 24.267;
var gBeta1default = 6.2209;
var gBeta2default = 0.5053;
var gThresholdProbabilityForMYCPOSdefault = 0.11;

var gIntercept;
var gBeta1;
var gBeta2;
var gThresholdProbabilityForMYCPOS;

var gUnitLogRegStatus;


//stat IOD all nuclei
var g_mean_iod_per_nucleus_all = 0;
var g_min_iod_per_nucleus_all = 0;
var g_max_iod_per_nucleus_all = 0;
var g_std_iod_per_nucleus_all = 0;


//stat IOD positive nuclei
var g_mean_iod_per_nucleus_pos = 0;
var g_min_iod_per_nucleus_pos = 0;
var g_max_iod_per_nucleus_pos = 0;
var g_std_iod_per_nucleus_pos = 0;


var gDEBUG = false;
var gINTERACTIVE;


var global_i=0;
var global_number_of_files = 0;
var global_array_dir;
var global_array_file;

var g_array_validPointsX;
var g_array_validPointsY;
var g_array_INVALIDPointsX;
var g_array_INVALIDPointsY;

var g_array_individual_IOD_all;
var g_array_individual_IOD_pos;

macro "AutoRun" {
	requires("1.49t"); //requires minimally imagej 1.49t especially for Plot functions
	close_auxiliary_windows();

	gUnitVectorsStatus = call("ij.Prefs.get", "myc.ihc.unit.vectors.deconvolution.status", "not determined");
	if (gUnitVectorsStatus == "not determined")
	{
	setDeconvolutionVectorsFromDefault();	
	call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.status", "determined");
	call("ij.Prefs.savePreferences"); // save preferences now
	}
	else
	{
	setDeconvolutionVectorsFromPrefs();	
	}
	
	gUnitLogRegStatus = call("ij.Prefs.get", "myc.ihc.log.reg.status", "not determined");
	if (gUnitLogRegStatus == "not determined")
	{
	setLogRegValuesFromDefault();	
	call("ij.Prefs.set", "myc.ihc.log.reg.status", "determined");
	call("ij.Prefs.savePreferences"); // save preferences now
	}
	else
	{
	setLogRegValuesFromPrefs();	
	}

	
}

macro "IHC MYC: Process One Picture Action Tool - C9ceD14D24D44D56D66D69D74D84D87D94D95Da7Db5Dc4Dc5Dc6Dc9Dd6C08dD02D03D11D21D31D41D51D61D70D80D90Da0Db0Dc1Dc2Dd3De3CdefD22D32D42D4bD52D5aD5bD5cD62D67D7fDbfDc0Dc7Dd9DdaDdbDdcDefDf3C07bD05D06D07D08D15D25D2eD35D3eD45D4eD55D8bD8cD9cDabDacDf5Df6Df7Df8CbdeD01D0fD13D23D33D43D53D60D63D73D83D93Da3Db3Dc3DecDfeC6adD39D3bD4dD5eD6aD6fD89D97D9dDa9DcaDcfDdeDe4DedCfffD00D10D20D30D40D50D71D72D81D82D8fD91D92Da1Da2DafDb1Dd0De0De1De2Df0Df1Df2DffC06aD09D0aD16D17D18D19D1aD1bD1cD7aD7bDbaDbbDf9DfaC9deD12D34D48D54D57D64D7dDa4Db4DbdDccDd4Dd7De8C29dD26D27D28D29D2aD2bD2cD36D37D38D3cD65D7cD8aD9aDaaDbcCeffD59D5dD68D6eD77D7eD86D96D9fDa6Db2Db7DbeDc8DceDd1DddC17bD04D78D98D9bDb8Df4CbefD49D4aD4cD58D6cD6dD76D8eD9eDaeDb6DcdDd8De9DeaDebC7beD3aD46D47D6bD75D85D8dD99Da5DadDcbDd2Dd5De5De6De7C059D0bD0cD1eD79D88Da8Db9DfbDfc"{
close_auxiliary_windows();	
oneAnalysis();	

}

macro "IHC MYC: Process Many Pictures in Folder Action Tool - Cfe7D13D15D19D25D29D35D39D45D49D55D59D65D69D75D78D79D89D96D99Da9Db9Dc9Dd9De3De9Cda2D0eD1cD1eD2cD2eD3cD3eD4cD4eD5cD5eD6cD6eD76D7cD7eD8cD8eD9cD9eDacDaeDbcDbeDccDceDdcDdeDecDeeDfeCffbDa6Db6Dc6Dd6De6Cfc1D2dD3dD4dD5dD67D6dD7dD8dD9dDadDbdDcdDddCfeaD32D62D97Da7Db7Dc7Dd7De7Cfd5D1aD3bD4aD6bD85DbaDdbCfffD00D01D0fD10D11D1fD20D2fD30D3fD40D4fD50D5fD60D6fD70D7fD80D81D8fD90D91D9fDa0Da1DafDb0Db1DbfDc0Dc1DcfDd0Dd1DdfDe0De1DefDf0Df1DffCfc0D02D03D04D12D22D31D41D51D61D72D82D92D95Da2Db2Db5Dc2Dc5Dd2Dd5De2De5Df2Df3Df4Df5Cfe9D14D21D24D34D44D54D64D71D74D84D88D94D98Da4Da8Db4Db8Dc4Dc8Dd4Dd8De4De8Cfd4D16D1bD26D2bD36D46D4bD56D5bD66D7bD8bD9bDabDbbDcbDebCffcD42D52Cfc2D17D27D37D47D57DedCffbD23D33D43D53D63D73D83D93Da3Db3Dc3Dd3Cfe6D2aD3aD5aD6aD7aD87D8aD9aDaaDcaDdaDeaCeb0D05D06D07D08D1dD38D68D77D86Da5Df6Df7"{
close_auxiliary_windows();	
batchAnalysis();	

}

macro "IHC MYC: Help Action Tool - C5adD05D0aD15D27D36D3dD50Da0Db2Db3DbcDc5Dc6DcdDd5Dd6De5Df5DfaC3aeD28D29D34D37D39D49D56D58D59D61D66D6dD6fD7eD9fDa9Db8Db9Dc9Dd8Dd9CeefD12D21D72D79D7dD95Dd1De2C29dD32D38D44D47D48D51D55D57D65D67D69D6aD6bDa1Dc2Dc8C7ceD17D18D24D33D4dD52D5eD5fD7bD84D98D9dDa2DaeDafDbdC4beD25D26D2aD3aD3bD3eD46D4aD4eD5aD6cD8eDaaDbaDbeDcaDcbDceDdaCfffD00D01D02D03D0cD0dD0eD0fD10D11D1eD1fD20D2fD30D3fD63D73D7cD82D83D87D88D89D8cD8dD93D94D96D97Da3Da4Da5Da6Dc0DcfDd0DdfDe0De1DeeDefDf0Df1Df2Df3DfcDfdDfeDffC37cD06D07D08D09D13D14D31D99D9aDc1De3De4Df6Df7Df8Df9C5cfD16D2bD3cD42D5dD6eDc3DccDd4Dd7DdbDe6De7C4beD1aD35D45D5cD71D75D7fD81D8fDabDacDc7DeaCfffD1dD2eD53D9cDdeDedC49dD1bD1cD23D2dD43D74D86D91D9bDa7Db6Dc4Dd3DddDebDecCbceD04D0bD40D4fD54D62D64D78D8bD92Db0Db4Db5DbfDf4DfbC5cfD19D2cD4bD4cD5bD9eDadDbbDdcDe8De9C07dD68D76D77D7aD85D8aDa8Db7"{

  showMessage("4/5", "<html>"
     +"<h1>IHC MYC</h1>"
     +"<h2>This software is licensed under MIT Licence</h2>"
     +"<h2>Copyright (c) 2016 Gilbert Bigras</h2>"
     +"<p>Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the \"Software\"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:</p>"
     +"<p>The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.</p>"
     +"<p>THE SOFTWARE IS PROVIDED \"AS IS\", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.</p>" 
     +"<h3>Prerequisites and software installation</h3>"
     +"<p>This software requires installation of imageJ, an open source software written in Java, available for Linux, Mac OS X and Windows. ImageJ is available <a href=\"https://imagej.nih.gov/ij/index.html\" target=\"_blank\">here</a>. Basic understanding of ImageJ will facilitate installation.</p>
     +"<p>Current software (MYC_IHC.txt) is a \"toolset\" written in macro language and requires to be installed in a precise directory: &rarr;ImageJ&rarr;macros&rarr;toolsets.</p>
     +"<p>Two additional \"plugins\" are required:</p>
     +"<ol>
     +"<li><strong><em>Color Deconvolution </em></strong>plugin written by Gabriel Landini is available <a href=\"http://www.mecourse.com/landinig/software/cdeconv/cdeconv.html\">here</a> with documentation.</li>
     +"<li><strong><em>Euclidean minimum spanning tree </em></strong>plugin written by Gilbert Bigras available <a href=\"http://imagejdocu.tudor.lu/doku.php?id=plugin:morphology:euclidean_minimum_spanning_tree:start\" target=\"_blank\">here</a>.</li>
     +"</ol>
     +"<p><strong><em>Colour deconvolution</em> </strong>and <strong><em>Euclidean minimum spanning tree</em></strong> plugin names are respectively: \"Colour_Deconvolution.class\" and \"e_mst.jar\". Both files (plugins) have to be installed in&nbsp;&rarr;ImageJ&rarr;plugins</p>
     +"<h3>Prerequisites for IHC analysis</h3>"
     +"<p>Since the purpose of this analysis is to be a predictor of MYC dysregulation, It is expected that pre-analytical and analytical factors related to tissue hansling are optimized and controlled as other <a href=\"http://www.ncbi.nlm.nih.gov/pubmed/26286753\" target=\"_blank\">class II Biomarkers</a></p>"
     +"<p>Operator is expected to grab an area of viable tumour with the most intense IHC staining</p>"
     +"<p>Operator is expected to grab a picture with <em>a priori</em> correction of background illumination as explained <a href=\"http://imagejdocu.tudor.lu/doku.php?id=howto:working:how_to_correct_background_illumination_in_brightfield_microscopy\" target=\"_blank\">here</a> by Gabriel Landini. This involves multiple steps a) Image acquisition of a white field without oversaturation and white balance of RGB channels b) Image acquisition of a black field c) Image acquisition of the tissue specimen and d) the correction itself.</p>"
     +"<h3>Software utilization</h3>"
     +"<p>Please find instruction here</p>"     
     
     );

}
var bCmds= newMenu("IHC MYC: Settings Menu Tool", newArray("Define Logistic Regression Params...","-","Define Color Deconvolution Params...","-","Reset Default Logistic Regression Params...","-","Reset Default Color Deconvolution Params..."));

macro "IHC MYC: Settings Menu Tool - C037D3eD4eD5eD6bD6cD6dD7aD89D98Da7Db6Dc6Dd6De4De5D2aD5dDa2Dd5D59D68D69D77D78D86D87D96D1aD1bD1cD29D2bD39D49D4bD4cD4dD58D67D76D85D92D93D94Da1Db1Db2Db4Dc1Dc4Dd4De3D5aD6aD79D88D95D97Da5Da6D19D91D4aD5bDa4Db5D3aD5cDa3Dc5" {
cmd= getArgument();

if (cmd!="-" && cmd == "Define Logistic Regression Params...")
{

			 title = "Set Logistic Regression Parameters";
			  Dialog.create("Set Logistic Regression Parameters");			  
			  Dialog.addNumber("Intercept (Beta0)", gIntercept);
			  Dialog.addNumber("Coefficient (Beta1) ratioEMST", gBeta1);
			  Dialog.addNumber("Coefficient (Beta2) CV", gBeta2);
			  Dialog.addNumber("Threshold POS", gThresholdProbabilityForMYCPOS);
			  Dialog.show();
			  
			  aIntercept = Dialog.getNumber();
			  aBeta1 = Dialog.getNumber();
			  aBeta2 = Dialog.getNumber();
			  aThresholdProbabilityForMYCPOS = Dialog.getNumber();

			  if((!isNaN(aIntercept)) && (!isNaN(aBeta1)) && (!isNaN(aBeta2)) && (!isNaN(aThresholdProbabilityForMYCPOS)))
			  {
			  call("ij.Prefs.set", "myc.ihc.log.reg.gIntercept",toString(aIntercept));
			  call("ij.Prefs.set", "myc.ihc.log.reg.gBeta1",toString(aBeta1));
			  call("ij.Prefs.set", "myc.ihc.log.reg.gBeta2",toString(aBeta2));
			  call("ij.Prefs.set", "myc.ihc.log.reg.gThresholdProbabilityForMYCPOS",toString(aThresholdProbabilityForMYCPOS));
			  call("ij.Prefs.savePreferences"); // save preferences now
			  setLogRegValuesFromPrefs();			  
			  }
			 else
			 {
			 	 warning("Values were not saved, please check integrity and retry");	  
			 }

			  

}
if (cmd!="-" && cmd == "Define Color Deconvolution Params...")
{
			 title = "Set vectors for color deconvolution";
			  Dialog.create("Set Vectors");
			  Dialog.addMessage("V1: Chromogen");			  
			  Dialog.addNumber("[R1]", gR1);
			  Dialog.addNumber("[G1]", gG1);
			  Dialog.addNumber("[B1]", gB1);
			  Dialog.addMessage("V2: Counterstain");			  
			  Dialog.addNumber("[R2]", gR2);
			  Dialog.addNumber("[G2]", gG2);
			  Dialog.addNumber("[B2]", gB2);
			  Dialog.addMessage("V3: Complementary");			  
			  Dialog.addNumber("[R3]", gR3);
			  Dialog.addNumber("[G3]", gG3);
			  Dialog.addNumber("[B3]", gB3);	  
			  Dialog.show();
			  
			  aR1 = Dialog.getNumber();
			  aG1 = Dialog.getNumber();
			  aB1 = Dialog.getNumber();
			  aR2 = Dialog.getNumber();
			  aG2 = Dialog.getNumber();
			  aB2 = Dialog.getNumber();
			  aR3 = Dialog.getNumber();
			  aG3 = Dialog.getNumber();
			  aB3 = Dialog.getNumber();
			
			 if((!isNaN(aR1)) && (!isNaN(aG1)) && (!isNaN(aB1)) && (!isNaN(aR2)) && (!isNaN(aG2)) && (!isNaN(aB2)) && (!isNaN(aR3)) && (!isNaN(aG3)) && (!isNaN(aB3)))
			 {
			 call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gR1",toString(aR1));
			 call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gG1",toString(aG1));
			 call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gB1",toString(aB1));
			 call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gR2",toString(aR2));
			 call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gG2",toString(aG2));
			 call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gB2",toString(aB2));
			 call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gR3",toString(aR3));
			 call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gG3",toString(aG3));
			 call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gB3",toString(aB3));
			 call("ij.Prefs.savePreferences"); // save preferences now
			 setDeconvolutionVectorsFromPrefs();// replace with new values
			 }
			 else
			 {
			 	 warning("Values were not saved, please check integrity and retry");	  
			 }
	
}
if (cmd!="-" && cmd == "Reset Default Logistic Regression Params...")
{
  	setLogRegValuesFromDefault();
	call("ij.Prefs.savePreferences"); // save preferences now	
	
}
if (cmd!="-" && cmd == "Reset Default Color Deconvolution Params...")
{
	setDeconvolutionVectorsFromDefault();
	call("ij.Prefs.savePreferences"); // save preferences now	
}

}	


function batchAnalysis() {
	 
	if (isOpen("CMYC_MST results")) { 
	  	  selectWindow("CMYC_MST results");
	  	  run("Close");
	 }
	if (isOpen("MYC IHC Plot")) { 
	  	  selectWindow("MYC IHC Plot");
	  	  run("Close");
	 }
	 

	 f = get_reference_table_results("CMYC_MST results");

	 dir = getDirectory("Choose a Directory ");
	 list = getFileList(dir);
	 titles = newArray(list.length);
	 run("Clear Results");
	
	
	if(gDEBUG) {
		cleanUp_Windows();
		close_auxiliary_windows();
		open("/home/gilbert/Pictures/CMYC/test2.tif");
		
	}
	
	initialize();
	cleanUp_Windows();
	gINTERACTIVE = false;
	
        for (k=0; k<list.length; k++)
        {		 
        	reset_var();
        	cleanUp_Windows();
        	showProgress(k/list.length);         	
 	setBatchMode(true);
 	path = dir+list[k];
 	open(path);
 
	
	if(nSlices>1)
	{
		openstack(nSlices);
		
		for(i=0;i<gNumberInStack;i++)
		{	
			cleanUp_Windows();
			sample = gDirStackTemp+"sample"+i+".tif";
			open(sample);
			rename("RGB");push("RGB");
			deconvolution("RGB");// to get DAB
			cleanUp_Windows();
			get("RGB");
			treatimage();
		}
	}
	else	// not a stack
	{	
		rename("RGB");push("RGB");
		deconvolution("RGB");// to get DAB and HEMA
		cleanUp_Windows();
		get("RGB");
		treatimage(); 
	}	
	
	//print("\\Clear");
	Array.getStatistics(g_array_individual_IOD_all,g_min_iod_per_nucleus_all, g_max_iod_per_nucleus_all, g_mean_iod_per_nucleus_all, g_std_iod_per_nucleus_all);
	Array.getStatistics(g_array_individual_IOD_pos,g_min_iod_per_nucleus_pos, g_max_iod_per_nucleus_pos, g_mean_iod_per_nucleus_pos, g_std_iod_per_nucleus_pos);
	
	n_all_nuclei = g_array_individual_IOD_all.length;
	n_Pos_nuclei = g_array_individual_IOD_pos.length;
	percentagePos =  n_Pos_nuclei / n_all_nuclei * 100;
	averageEdgeAll = g_Sum_Edge_distance_all_points/g_Number_Edge_all_points;
	averageEdhePos = g_Sum_Edge_distance_pos_points/g_Number_Edge_pos_points;
	ratioEMST = averageEdhePos / averageEdgeAll;
	coefficientVariation = g_std_iod_per_nucleus_pos/g_mean_iod_per_nucleus_pos*100;
	
	prob=computeLogFunction(gIntercept,gBeta1,gBeta2,ratioEMST,coefficientVariation);
	if (prob > gThresholdProbabilityForMYCPOS)
		{
			status="POSITIVE";
		}
	else
		{
			status="NEGATIVE";
		}
	
	

	
	print(f, list[k] + "\t" +d2s(ratioEMST,4) + "\t" +g_mean_iod_per_nucleus_all+ "\t" +coefficientVariation + "\t" + percentagePos + "\t"+prob + "\t" + status );
	close_auxiliary_windows();
	
        }
        //print("End of analyze");
}

function oneAnalysis() {
	 
	if (isOpen("CMYC_MST results")) { //close first; might be present but hidden; then re-open
	  	  selectWindow("CMYC_MST results");
	  	  run("Close");
	 }
	if (isOpen("MYC IHC Plot")) { 
	  	  selectWindow("MYC IHC Plot");
	  	  run("Close");
	 }
	 
	 
	 if(bitDepth() < 24)
	 {
	 	 warning("A 24 bits color picture is expected");
	 	 exit();
	 }
	 
	 filename = File.name;
	 f = get_reference_table_results("CMYC_MST results");
	 run("Clear Results");
	
	
	
	initialize();
	
	gINTERACTIVE = true;
	 
        	reset_var(); 	 
         	
 	setBatchMode(true); 
	
	if(nSlices>1)
	{
		openstack(nSlices);
		
		for(i=0;i<gNumberInStack;i++)
		{	
			cleanUp_Windows();
			sample = gDirStackTemp+"sample"+i+".tif";
			open(sample);
			rename("RGB");push("RGB");
			deconvolution("RGB");// to get DAB
			cleanUp_Windows();
			get("RGB");
			treatimage();
		}
	}
	else	// not a stack
	{	
		rename("RGB");push("RGB");
		deconvolution("RGB");// to get DAB and HEMA
		cleanUp_Windows();
		get("RGB");
		treatimage(); 
	}	
	
	//print("\\Clear");
	Array.getStatistics(g_array_individual_IOD_all,g_min_iod_per_nucleus_all, g_max_iod_per_nucleus_all, g_mean_iod_per_nucleus_all, g_std_iod_per_nucleus_all);
	Array.getStatistics(g_array_individual_IOD_pos,g_min_iod_per_nucleus_pos, g_max_iod_per_nucleus_pos, g_mean_iod_per_nucleus_pos, g_std_iod_per_nucleus_pos);
	
	n_all_nuclei = g_array_individual_IOD_all.length;
	n_Pos_nuclei = g_array_individual_IOD_pos.length;
	percentagePos =  n_Pos_nuclei / n_all_nuclei * 100;
	averageEdgeAll = g_Sum_Edge_distance_all_points/g_Number_Edge_all_points;
	averageEdhePos = g_Sum_Edge_distance_pos_points/g_Number_Edge_pos_points;
	ratioEMST = averageEdhePos / averageEdgeAll;
	coefficientVariation = g_std_iod_per_nucleus_pos/g_mean_iod_per_nucleus_pos*100;
	
	prob=computeLogFunction(gIntercept,gBeta1,gBeta2,ratioEMST,coefficientVariation);
	if (prob > gThresholdProbabilityForMYCPOS)
		{
			status="POSITIVE";
		}
	else
		{
			status="NEGATIVE";
		}
	

	
	print(f, filename + "\t" +d2s(ratioEMST,4) + "\t" +g_mean_iod_per_nucleus_all+ "\t" +coefficientVariation + "\t" + percentagePos + "\t"+prob + "\t" + status );
		
	xPatient = newArray(1);
	yPatient = newArray(1);
	xPatient[0] = ratioEMST;
	yPatient[0] = coefficientVariation;
	textCase = "Case: "+filename+"\n"+"Probability MYC+: "+prob+" %"+"\n"+"MYC Status: "+status;
	
	
	Plot.create("MYC IHC Plot", "EMST ratio", "Coefficient of Variation");
	Plot.setLimits(1.0, 4.5, 20, 60);
	Plot.setColor("gray", "gray");
	Plot.add("circle", gArrayPOSratioEMST, gArrayPOSCV);
	Plot.setColor("black", "white");
	Plot.add("circle", gArrayNEGratioEMST, gArrayNEGCV);
	Plot.setColor("black", "black");
	Plot.add("box", xPatient, yPatient);
	Plot.addLegend("MYC POS\nMYC NEG\nPatient");
	Plot.addText(textCase,0.5,0.8);
	//Plot.makeHighResolution("MYC IHC Plot_HiRes",4.0);
	//Plot.update();
	//run("Rotate 90 Degrees Right");
	
	
	
	close_auxiliary_windows();
	
  
	
}

 function get_reference_table_results(title1)
	{
		requires("1.43g");
		//title1 = "HER2 intensity(Signal Mask)";
		title2 = "["+title1+"]";
		f = title2;
		if (isOpen(title1))
		print(f, "\\Clear");
		else {
			if (getVersion>="1.41g")
			run("Table...", "name="+title2+" width=800 height=400");
			else
			run("New... ", "name="+title2+" type=Table width=800 height=600");
			}
		print(f, "\\Headings:Case\tRatio EMST\tAverage (all) IOD\tCV IOD pos\tPercentage pos\tProbability MYC+\tMYC Status");
		return f;
	}
	
function initialize()
 {	
 	g_Sum_Edge_distance_all_points=0;
 	g_Number_Edge_all_points=0;
 	g_Sum_Edge_distance_pos_points=0;
 	g_Number_Edge_pos_points=0;
 	
 	g_iTotalNuclei=0;
 	g_iSizeMatrixSampling=0;
 	
	for(i=-g_MatrixSamplingCounter;i<=g_MatrixSamplingCounter;i++)
		{
		g_iSizeMatrixSampling++;		
		}
	
	g_iSizeMatrixSampling = (g_iSizeMatrixSampling*g_iSizeMatrixSampling);	

	
	gDirParameters = getDirectory("imagej");
	
	
	gDirStackTemp = gDirParameters+"StackTemp"+File.separator;	
	File.makeDirectory(gDirStackTemp);
	
 }
 
 function reset_var()
 {
 	g_array_individual_IOD_all = newArray();
 	g_array_individual_IOD_pos = newArray();
 	
 	g_Sum_Edge_distance_all_points=0;
 	g_Number_Edge_all_points=0;
 	g_Sum_Edge_distance_pos_points=0;
 	g_Number_Edge_pos_points=0;
 
	g_iTotalNuclei=0;

 	g_mean_iod_per_nucleus_all=0;
 	g_min_iod_per_nucleus_all=0;
 	g_max_iod_per_nucleus_all=0;
 	g_std_iod_per_nucleus_all=0;
 	
 	g_mean_iod_per_nucleus_pos = 0;
 	g_min_iod_per_nucleus_pos = 0;
 	g_max_iod_per_nucleus_pos = 0;
 	g_std_iod_per_nucleus_pos = 0;
 	g_maxrange_iod_nuclei_pos = 0;
 
 }
 

function treatimage()
 {
	run("Mean...", "radius=2");
	
	Instable = true;
	noise = 0;
	setBatchMode(true);
	
	
	while(Instable) {
		run("Find Maxima...", "noise=&noise output=Count exclude light");
		count = getResult("Count");
		gCount[noise]=count;		
		Instable = checkStability(noise);
		if(Instable) {noise = noise +1;}
	}
	
	close_auxiliary_windows();
	/*
	if(gINTERACTIVE)
	{		
	setBatchMode(false);
	run("Find Maxima...", "noise=&noise output=[Point Selection] exclude light");
	setTool("hand");
	waitForUser("Please inspect result");
	setBatchMode(true);
	}
	*/
	
	//find all nuclei
	cleanUp_Windows();
	get("RGB");
	run("Mean...", "radius=2");
	run("Find Maxima...", "noise=&noise output=List exclude light");
	maxpoint = nResults;
	find_all_points(maxpoint);
	
	//dump();
	//exit();
	
	/*
	if(gINTERACTIVE)
	{	
		setBatchMode(false);
		selectWindow("RGB");
		setTool("hand");
		waitForUser("Please inspect result, after removing too clear objects");
		setBatchMode(true);
	}
	//exit();
	*/	
	
	selectWindow("RGB");
	run("Select None");
	run("Point Tool...", "selection=Black cross=White marker=Small");
	makeSelection("points",g_array_validPointsX,g_array_validPointsY);
	
	
	run("EMST", "color=Green approximate=3000 export");	
	iEdge_in_current_slice = nResults;
	
	if(gINTERACTIVE)
	{	
		setBatchMode(false);
		selectWindow("RGB");
		setTool("hand");
		waitForUser("Please inspect result - EMST with all nuclei and click OK");
		setBatchMode(true);
	}

	cleanUp_Windows();
	g_Number_Edge_all_points = g_Number_Edge_all_points + iEdge_in_current_slice;
	for(n=0;n<iEdge_in_current_slice;n++)
	{	
		x0=getResult("X0",n);
		y0=getResult("Y0",n);
		x1=getResult("X1",n);
		y1=getResult("Y1",n);

		g_Sum_Edge_distance_all_points = g_Sum_Edge_distance_all_points + distance(x0,y0,x1,y1);	
	}
	
	//find pos nuclei
	get(gDAB);
	selectWindow(gDAB);
	run("Calibrate...", "function=[Uncalibrated OD] unit=[Gray Value] text1= text2=");
	//run("Median...", "radius=5");
	setAutoThreshold("MaxEntropy");
	getThreshold(lower,upper); //lower is darker with bacground white ... so use upper
	
	/*
	if(gINTERACTIVE)
	{	
		setBatchMode(false);
		get("RGB");
		selectWindow("RGB");
		run("Add Image...", "&gDAB x=0 y=0 opacity=25");
		waitForUser("Please inspect result");
		setBatchMode(true);
	}
	*/
	
	cleanUp_Windows();
	get("RGB");
	run("Mean...", "radius=2");
	run("Find Maxima...", "noise=&noise output=List exclude light");
	maxpoint = nResults;
	
	findPositiveNuclei(maxpoint,upper);
	selectWindow("RGB");
	run("Select None");
	run("Point Tool...", "selection=Black cross=White marker=Small");
	makeSelection("points",g_array_validPointsX,g_array_validPointsY);
	
	
	
	run("EMST", "color=Green approximate=3000 export");	
	
	if(gINTERACTIVE)
	{	
		setBatchMode(false);
		waitForUser("Please inspect result - EMST with positive nuclei only and click OK");
		setBatchMode(true);
	}

	iEdge_in_current_slice = nResults;
	cleanUp_Windows();
	g_Number_Edge_pos_points = g_Number_Edge_pos_points + iEdge_in_current_slice;
	for(n=0;n<iEdge_in_current_slice;n++)
	{	
		x0=getResult("X0",n);
		y0=getResult("Y0",n);
		x1=getResult("X1",n);
		y1=getResult("Y1",n);
		
		dist = distance(x0,y0,x1,y1);

		g_Sum_Edge_distance_pos_points = g_Sum_Edge_distance_pos_points + dist;	
	}

	
	
 }
 function setDeconvolutionVectorsFromPrefs()
 	{
	gR1=parseFloat(call("ij.Prefs.get", "myc.ihc.unit.vectors.deconvolution.gR1","")); //"" is the default value but should never be called. Inserted here to respect number of arguments 
	gG1=parseFloat(call("ij.Prefs.get", "myc.ihc.unit.vectors.deconvolution.gG1",""));
	gB1=parseFloat(call("ij.Prefs.get", "myc.ihc.unit.vectors.deconvolution.gB1",""));
	gR2=parseFloat(call("ij.Prefs.get", "myc.ihc.unit.vectors.deconvolution.gR2",""));
	gG2=parseFloat(call("ij.Prefs.get", "myc.ihc.unit.vectors.deconvolution.gG2",""));
	gB2=parseFloat(call("ij.Prefs.get", "myc.ihc.unit.vectors.deconvolution.gB2",""));
	gR3=parseFloat(call("ij.Prefs.get", "myc.ihc.unit.vectors.deconvolution.gR3",""));
	gG3=parseFloat(call("ij.Prefs.get", "myc.ihc.unit.vectors.deconvolution.gG3",""));
	gB3=parseFloat(call("ij.Prefs.get", "myc.ihc.unit.vectors.deconvolution.gB3",""));	
	}

function setDeconvolutionVectorsFromDefault()
 	{
	gR1=gR1default;
	call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gR1",toString(gR1));
	gG1=gG1default;
	call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gG1",toString(gG1));
	gB1=gB1default;
	call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gB1",toString(gB1));
	gR2=gR2default;
	call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gR2",toString(gR2));
	gG2=gG2default;
	call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gG2",toString(gG2));
	gB2=gB2default;
	call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gB2",toString(gB2));
	gR3=gR3default;
	call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gR3",toString(gR3));
	gG3=gG3default;
	call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gG3",toString(gG3));
	gB3=gB3default;
	call("ij.Prefs.set", "myc.ihc.unit.vectors.deconvolution.gB3",toString(gB3));	
	}

 function setLogRegValuesFromPrefs()
 	{
	gIntercept=parseFloat(call("ij.Prefs.get", "myc.ihc.log.reg.gIntercept","")); //"" is the default value but should never be called. Inserted here to respect number of arguments 
	gBeta1=parseFloat(call("ij.Prefs.get", "myc.ihc.log.reg.gBeta1",""));
	gBeta2=parseFloat(call("ij.Prefs.get", "myc.ihc.log.reg.gBeta2",""));
	gThresholdProbabilityForMYCPOS=parseFloat(call("ij.Prefs.get", "myc.ihc.log.reg.gThresholdProbabilityForMYCPOS",""));
	}

function setLogRegValuesFromDefault()
	{
	gIntercept=gInterceptdefault;
	call("ij.Prefs.set", "myc.ihc.log.reg.gIntercept",toString(gIntercept));
	gBeta1=gBeta1default;
	call("ij.Prefs.set", "myc.ihc.log.reg.gBeta1",toString(gBeta1));
	gBeta2=gBeta2default;
	call("ij.Prefs.set", "myc.ihc.log.reg.gBeta2",toString(gBeta2));
	gThresholdProbabilityForMYCPOS=gThresholdProbabilityForMYCPOSdefault;
	call("ij.Prefs.set", "myc.ihc.log.reg.gThresholdProbabilityForMYCPOS",toString(gThresholdProbabilityForMYCPOS));
	}

function deconvolution(rgbsample)
 {
	selectImage(rgbsample);
	//run("Colour Deconvolution", "vectors=HemaHarris_DAB_CCI");
	run("Colour Deconvolution", "vectors=[User values] [r1]=gR1 [g1]=gG1 [b1]=gB1 [r2]=gR2 [g2]=gG2 [b2]=gB2 [r3]=gR3 [g3]=gG3 [b3]=gB3");
	selectWindow(rgbsample+"-(Colour_1)");
	rename(gDAB);
	push(gDAB);
	selectWindow(rgbsample+"-(Colour_2)");
	rename(gHEMA);
	push(gHEMA);
	
	cleanUp_Windows();	
}

function openstack(nSamples)
 {	
	//setBatchMode(true);
	gNumberInStack = nSamples; //initialization
	gStackName = getTitle();
	run("Stack to Images");
	while (nImages()>0)
	{
		selectImage(nImages());
		//print(gDirStackTemp);
		//print(getTitle());
		//exit();
		saveAs("tiff",gDirStackTemp+getTitle());
		run("Close");
	}
	//setBatchMode(false);
 }

function push(tempname)
 {
	selectImage(tempname);
	save(gDirStackTemp+tempname+".tif");	
 }
 
function get(tempname)
 {
	open(gDirStackTemp+tempname+".tif");
	rename(tempname);
 }
 
 function getIOD(x,y)
  {
  	dabintensity = 0;
		
  	  	for(i=-g_MatrixSamplingCounter;i<=g_MatrixSamplingCounter;i++) 
		  for(j=-g_MatrixSamplingCounter;j<=g_MatrixSamplingCounter;j++)
		  {
		   dabintensity = dabintensity + calibrate(getPixel(x+i,y+j));
		  }
		
	return (dabintensity/g_iSizeMatrixSampling);
  	  
  }

function checkStability(noise)
 {
	if(noise < 2) {return true;}
	//print("gCount = "+gCount[noise]+" for noise = "+noise);
	//print("gCount = "+gCount[noise-1]+" for noise-1 = "+noise-1);
	percentage1 = (gCount[noise-1] - gCount[noise])/gCount[noise-1]*100;
	//print("percentage1 = ",percentage1);
	percentage2 = (gCount[noise-2] - gCount[noise-1])/gCount[noise-2]*100;
	//print("percentage2 = ",percentage2);
	
	if ((percentage2 - percentage1) < 1)
	{
		return false; //means stability achieved 
	}
	else
	{
		return true; // still instable
	}
	
		
 }
function cleanUp_Windows()
 {
		requires("1.30e");
		while (nImages()>0)
		{
			selectImage(nImages());  
			run("Close");
		}
 }



function close_auxiliary_windows()
 {
	  if (isOpen("ROI Manager")) {
	  	  selectWindow("ROI Manager");
	  	  run("Close");
	  }
	  if (isOpen("Results")) {
	  	  selectWindow("Results");
	  	  run("Close");
	  }
	  if (isOpen("Log")) {
	  	  selectWindow("Log");
	  	  run("Close");
	  }
 }
  
function find_all_points(maxpossiblepoints)
{	
	
	get(gDAB);
	run("Calibrate...", "function=[Uncalibrated OD] unit=[Gray Value] text1= text2=");
	get(gHEMA);
	run("Calibrate...", "function=[Uncalibrated OD] unit=[Gray Value] text1= text2=");
	
	g_array_validPointsX = newArray(maxpossiblepoints);
	g_array_validPointsY = newArray(maxpossiblepoints);
	local_array_individual_IOD_all = newArray(maxpossiblepoints);
	g_array_INVALIDPointsX = newArray(maxpossiblepoints);
	g_array_INVALIDPointsY = newArray(maxpossiblepoints);
	
	iValidPoints = 0;
	iINVALIDPoints = 0;
	
	
	
	for(n=0;n<maxpossiblepoints;n++)
	{	
		x=getResult("X",n);
		y=getResult("Y",n);
		
		selectWindow(gDAB);
		dabintensity = 0;
		
		for(i=-g_MatrixSamplingCounter;i<=g_MatrixSamplingCounter;i++) 
		  for(j=-g_MatrixSamplingCounter;j<=g_MatrixSamplingCounter;j++)
		  {
		   dabintensity = dabintensity + calibrate(getPixel(x+i,y+j));
		  }
		
		  dabintensity = dabintensity/(g_iSizeMatrixSampling);
		  
		  
		  if(dabintensity <= 0.0948) // This is quite pale .... verify this is a negative "blue" nucleus by testing the corresponding HEMA intensity
		  	{
		  	 	
		  	  selectWindow(gHEMA);
		  	  hemaintensity = 0;
		
		  	  for(ii=-g_MatrixSamplingCounter;ii<=g_MatrixSamplingCounter;ii++) 
		  	  	  for(jj=-g_MatrixSamplingCounter;jj<=g_MatrixSamplingCounter;jj++)
		  	  	  {
		  	  	  hemaintensity = hemaintensity + calibrate(getPixel(x+ii,y+jj));
		  	  	  }
		
		  	  	  hemaintensity = hemaintensity/g_iSizeMatrixSampling;
		  	  	  
		  	  	  if(hemaintensity>gMINIMUM_HEMATOX) //OK it is a nucleus... register the point
		  	  	  {
		  	  	  	  g_array_validPointsX[iValidPoints] = x;
		  	  	  	  g_array_validPointsY[iValidPoints] = y;
		  	  	  	  local_array_individual_IOD_all[iValidPoints] = dabintensity;
		  	  	  	  iValidPoints++;
		  	  	  	  g_iTotalNuclei++;
		  	  	  }
		  	  	  else
		  	  	 {
		  	  	  	  g_array_INVALIDPointsX[iINVALIDPoints] = x;
		  	  	  	  g_array_INVALIDPointsY[iINVALIDPoints] = y;
		  	  	  	  iINVALIDPoints++;
		  	  	 }
		  	}
		  
		else
			{
		  	  	  	  g_array_validPointsX[iValidPoints] = x;
		  	  	  	  g_array_validPointsY[iValidPoints] = y;
		  	  	  	  local_array_individual_IOD_all[iValidPoints] = dabintensity;
		  	  	  	  iValidPoints++;
		  	  	  	  g_iTotalNuclei++;
			}		
		
	}
	
	
	g_array_validPointsX = Array.trim(g_array_validPointsX,iValidPoints);
	g_array_validPointsY = Array.trim(g_array_validPointsY,iValidPoints);
	local_array_individual_IOD_all = Array.trim(local_array_individual_IOD_all,iValidPoints);
	
	g_array_individual_IOD_all = Array.concat(g_array_individual_IOD_all,local_array_individual_IOD_all);
	//Array.print(g_array_individual_IOD_all);
	
	g_array_INVALIDPointsX = Array.trim(g_array_INVALIDPointsX,iINVALIDPoints);
	g_array_INVALIDPointsY = Array.trim(g_array_INVALIDPointsY,iINVALIDPoints);
	
	selectWindow("RGB");
	run("Select None");
	run("Point Tool...", "selection=Black cross=White marker=Small");
	makeSelection("points",g_array_validPointsX,g_array_validPointsY);
	
	

}
function findPositiveNuclei(maxpossiblepoints,threshold)
{	
	
	get(gDAB);
	run("Calibrate...", "function=[Uncalibrated OD] unit=[Gray Value] text1= text2=");
	g_array_validPointsX = newArray(maxpossiblepoints);
	g_array_validPointsY = newArray(maxpossiblepoints);
	local_array_individual_IOD_pos = newArray(maxpossiblepoints);
	
	iValidPoints = 0;
	
	
	for(n=0;n<maxpossiblepoints;n++)
	{	
		//print("entered in pos loop");
		x=getResult("X",n);
		y=getResult("Y",n);
		
		selectWindow(gDAB);
		dabintensity = 0;
		
		dabintensity = getIOD(x,y);
		
		
		//print(dabintensity);
		
		if(dabintensity >= threshold)
		{
		 g_array_validPointsX[iValidPoints] = x;
		 g_array_validPointsY[iValidPoints] = y;
		 local_array_individual_IOD_pos[iValidPoints] = dabintensity;
		 iValidPoints++;	
		}
	}
	
	g_array_validPointsX = Array.trim(g_array_validPointsX,iValidPoints);
	g_array_validPointsY = Array.trim(g_array_validPointsY,iValidPoints);
	local_array_individual_IOD_pos = Array.trim(local_array_individual_IOD_pos,iValidPoints);
	
	g_array_individual_IOD_pos = Array.concat(g_array_individual_IOD_pos,local_array_individual_IOD_pos);
	
	cleanUp_Windows();
	get("RGB");
	selectWindow("RGB");
	run("Select None");
	run("Point Tool...", "selection=Black cross=White marker=Small");
	makeSelection("points",g_array_validPointsX,g_array_validPointsY);



	
}




function distance(x0,y0,x1,y1)
{
	return (sqrt((x0-x1)*(x0-x1)+(y0-y1)*(y0-y1)));
}

function warning(a_message)
{
	Dialog.create("WARNING!");
	Dialog.addMessage(a_message);
	Dialog.show();

}

function computeLogFunction(intercept,beta1,beta2,ratioEMST,CV)
{	
	interim1 = -1*(intercept-beta1*ratioEMST-beta2*CV);
	interim2 = exp(interim1);
	prob = 100*(1/(1+interim2));
	return (prob);
}
	
