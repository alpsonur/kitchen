-------------------------------------------------------------------------------
# Program version Allplan Bridge 2023-0-2
# Database version 1.04
#-------------------------------------------------------------------------------

ABM BEGIN
	
	#---------------------------------------------------------------------------
	# General project settings
	#---------------------------------------------------------------------------
	
	PROJECT BEGIN
		
		IFC        OBJTYPE          "IfcBridge:ARCHED"
		
		UNIT       SETDB ANGLED     "\[deg\]"    ""      "Degree to Radians"
		UNIT       SETDB ANGLE      "\[rad\]"    ""      "Radians"
		UNIT       SETDB LCROSSD    "\[m\]"      ""      "Meter"
		UNIT       SETDB LCROSS     "\[m\]"      ""      "Meter"
		UNIT       SETDB LSTRUCTD   "\[m\]"      ""      "Meter"
		UNIT       SETDB LSTRUCT    "\[m\]"      ""      "Meter"
		UNIT       SETDB STATION    "\[m\]"      ""      "Meter"
		UNIT       SETDB TEMP       "\[°C\]"     ""      "Celsius for temperature "
		UNIT       SETDB AREINF     "\[cm²\]"    ""      "Square Centimeter to Square Meter"
		UNIT       SETDB ASTRAND    "\[mm²\]"    ""      "Square Millimeter to Square Meter"
		UNIT       SETDB EMOD       "\[N/mm²\]"  ""      "Stress to Kilonewton per Square Meter"
		UNIT       SETDB STRESS     "\[N/mm²\]"  ""      "Stress to Kilonewton per Square Meter"
		UNIT       SETDB FORCE      "\[kN\]"     ""      "Kilonewton"
		UNIT       SETDB MOMENT     "\[kNm\]"    ""      "Kilonewton Meter"
		UNIT       SETDB DEVIATION  "\[rad/m\]"  ""      "Radian per Meter"
		UNIT       SETDB LSMALL     "\[mm\]"     ""      "Millimeter to Meter"
		UNIT       SETDB GAMMA      "\[kN/m³\]"  ""      "Specific weight Kilonewton per Meter³"
		UNIT       SETDB ACC        "\[m/s²\]"   ""      "Acceleration Meter per Second²"
		
		PORIGIN                 0.000                0.000
		RADIUS+    LEFT
		
		#-----------------------------------------------------------------------
		# Recalculation settings (analysis)
		#-----------------------------------------------------------------------
		
		RECALCULATION BEGIN
			
			OPTION   TIMELINE                 ON
			
			STRUCTURE BEGIN
				
				ANALYSISMODEL                 OFF
				
			STRUCTURE END
			
		RECALCULATION END
		
	PROJECT END
	
	#---------------------------------------------------------------------------
	# Standard EC2
	#---------------------------------------------------------------------------
	
	STANDARD "EN" BEGIN
		
		MATERIALS "@concrete" BEGIN
			
			MATERIAL "C35/45" BEGIN
				
				TEXT        ""
				FOREIGN     "EN_Eurocode:C_35/45"
				
				VALUES BEGIN
					
					VALUE   EMODUL    "E"            34100                    "\%0.0lf" ""
					VALUE   GMODUL    "G"            14208.3                  "\%0.0lf" ""
					VALUE   POISSON   "Ny"           0.2                      "\%0.1lf" ""
					VALUE   ALPHAT    "Alpha-T"      1E-05                    "\%0.6lf" ""
					VALUE   GAMMA     "Gamma"        24.5166                  "\%0.1lf" ""
					VALUE   FCK       "fck"          35                       "\%0.0lf" ""
					VALUE   FCM       "fcm"          43                       "\%0.0lf" ""
					VALUE   CEMENTCLASS "Cement class" 1                      "\%0.3lf" ""
					VALUE   CAGGREGATE "Concrete Aggregate" QUARTZITE         ""        ""
					VALUE   GCEMENT   "Cement Content" 0                      "\%0.1lf" ""
					VALUE   GSILICATE "Silicate Content" 0                    "\%0.1lf" ""
					
				VALUES END
				
			MATERIAL END
			
		MATERIALS END
		
		MATERIALS "@prestress_steel" BEGIN
			
			MATERIAL "Y1860S7-15,2" BEGIN
				
				TEXT        ""
				FOREIGN     ""
				
				VALUES BEGIN
					
					VALUE   EMODUL    "E"            195000                   "\%0.0lf" ""
					VALUE   GMODUL    "G"            84782.6                  "\%0.0lf" ""
					VALUE   POISSON   "Ny"           0.15                     "\%0.1lf" ""
					VALUE   ALPHAT    "Alpha-T"      1E-05                    "\%0.6lf" ""
					VALUE   GAMMA     "Gamma"        76.9822                  "\%0.1lf" ""
					VALUE   FPK       "fpk"          1860                     "\%0.0lf" ""
					VALUE   FP01K     "fp01k"        1640                     "\%0.0lf" ""
					VALUE   EPS_UD    "eps_ud"       0.028                    "\%0.3lf" ""
					VALUE   EPS_UK    "eps_uk"       0.035                    "\%0.3lf" ""
					VALUE   SIGPMAX   "Sig-pm0"      1394                     "\%0.0lf" ""
					VALUE   RELAXCLASS "Relaxation class" 2                   "\%d"     ""
					
				VALUES END
				
			MATERIAL END
			
		MATERIALS END
		
		MATERIALS "@reinf_steel" BEGIN
			
			MATERIAL "B 500B" BEGIN
				
				TEXT        ""
				FOREIGN     "EN_Eurocode:St500(B)"
				
				VALUES BEGIN
					
					VALUE   EMODUL    "E"            200000                   "\%0.0lf" ""
					VALUE   GMODUL    "G"            83333.3                  "\%0.0lf" ""
					VALUE   POISSON   "Ny"           0.2                      "\%0.1lf" ""
					VALUE   ALPHAT    "Alpha-T"      1E-05                    "\%0.6lf" ""
					VALUE   GAMMA     "Gamma"        76.9822                  "\%0.1lf" ""
					VALUE   FYK       "fyk"          500                      "\%0.0lf" ""
					VALUE   REINFCLASS "Reinforcement Class" CLASSB           ""        ""
					
				VALUES END
				
			MATERIAL END
			
		MATERIALS END
		
	STANDARD END
	
	#---------------------------------------------------------------------------
	# Axes definition
	#---------------------------------------------------------------------------
	
	AXES BEGIN
		
		AXIS "Axis" BEGIN
			
			BIMPLUS         "" ""
			
			SSLOPE          ASC
			SBEGIN                           0
			
			PLAN BEGIN
				
				POINT       ABS                   0               0               0
				LINE        DS                   50
				
			PLAN END
			
			PROFILES BEGIN
				
				PROFILE "Profile" ACTIVE BEGIN
					
					SCALE       10
					
					POLYGON BEGIN
						
						POINT            0.000000     1.000000
						POINT           25.000000    12.000000   PARADST      25.000000      25.000000
						POINT           50.000000     1.000000
						
					POLYGON END
					
				PROFILE END
				
			PROFILES END
			
		AXIS END
		
		AXIS "SecondaryAxis_1" BEGIN
			
			BIMPLUS         "" ""
			
			SSLOPE          ASC
			SBEGIN                           0
			
			PLAN BEGIN
				
				POINT       ABS                 -30              32      -33.367013
				CIRCLE      DSR             116.473             100
				
			PLAN END
			
			PROFILES BEGIN
				
				PROFILE "Profile" ACTIVE BEGIN
					
					SCALE       10
					
					POLYGON BEGIN
						
						POINT            0.000000     0.000000
						POINT          116.473000     0.000000
						
					POLYGON END
					
				PROFILE END
				
			PROFILES END
			
		AXIS END
		
		AXIS "SecondaryAxis_2" BEGIN
			
			BIMPLUS         "" ""
			
			SSLOPE          ASC
			SBEGIN                           0
			
			PLAN BEGIN
				
				POINT       ABS                 -30             -32       33.367013
				CIRCLE      DSR             116.473            -100
				
			PLAN END
			
			PROFILES BEGIN
				
				PROFILE "Profile" ACTIVE BEGIN
					
					SCALE       10
					
					POLYGON BEGIN
						
						POINT            0.000000     0.000000
						POINT          116.473000     0.000000
						
					POLYGON END
					
				PROFILE END
				
			PROFILES END
			
		AXIS END
		
		AXIS "Trans Axis 1" SECONDARY BEGIN
			
			REFAXIS         "Axis"        0.000000
			DS                           40
			DALPHAP                       0
			ALPHAE                        0
			HCROSS                  0.00000
			
		AXIS END
		
		AXIS "Trans Axis 2" SECONDARY BEGIN
			
			REFAXIS         "Axis"       50.000000
			DS                           40
			DALPHAP                       0
			ALPHAE                        0
			HCROSS                  0.00000
			
		AXIS END
		
	AXES END
	
	#---------------------------------------------------------------------------
	# Calculator - Formulas, Functions, Tables 
	#---------------------------------------------------------------------------
	
	CALC BEGIN
		
		TABLE      "Height"          ""
		
		CURVE "Height"   CONSTX   CONSTY BEGIN
			
			LINE            "23.2365" "1"
			PARA0E          "38.2365" "5"
			LINE            "55.7365" "7"
			PARA0B          "60.7365" "7"
			LINE            "78.2365" "5"
			LINE            "93.2365" "1"
			
		CURVE END
		
	CALC END
	
	#---------------------------------------------------------------------------
	# Cross sections
	#---------------------------------------------------------------------------
	
	CSECTIONS BEGIN
		
		CSECTION "Bridge" BEGIN
			
			TEXT   ""
			
			CVARS BEGIN
				
				VAR         "RefL"                   -15.00000  LENGTH  ""
				VAR         "RefR"                    15.00000  LENGTH  ""
				
			CVARS END
			
			CLINES BEGIN
				
				ZAXIS       "Zloc"              0.00000      0.00000
				YAXIS       "Yloc"              0.00000     90.00000
				
				PARALLEL    "L1"           "RefL"         NEG  LINE   "Yloc"
				PARALLEL    "L2"           "RefR"         NEG  LINE   "Yloc"
				PARALLEL    "L3"                1.00000   NEG  LINE   "Zloc"
				
			CLINES END
			
			CBOUNDARIES BEGIN
				
				BOUNDARY "Boundary 1" BEGIN
					
					POINTS BEGIN
						
						BPOINT       1  LSECT   "L1"    "Zloc"
						BPOINT       2  LSECT   "L1"    "L3"
						BPOINT       3  LSECT   "L2"    "L3"
						BPOINT       4  LSECT   "L2"    "Zloc"
						
					POINTS END
					
				BOUNDARY END
				
			CBOUNDARIES END
			
			CUNITS BEGIN
				
				SBEAM       1    LSECT     "Zloc"    "Yloc"
				
				SBEAM       1    BOUNDARY  "Boundary 1"
				
			CUNITS END
			
			CPROPSETS 1 BEGIN
				
				PROPERTY    IFC            OBJTYPE        "IfcSlab:TRACKSLAB"
				PROPERTY    IFC            OBJNAME        "Deck slab"
				
			CPROPSETS END
			
		CSECTION END
		
		CSECTION "Wingwall" BEGIN
			
			TEXT   ""
			
			CVARS BEGIN
				
				VAR         "Offset"                   0.00000  LENGTH  ""
				VAR         "Height"                   5.00000  LENGTH  ""
				VAR         "Bottom"                  -0.50826  LENGTH  ""
				
			CVARS END
			
			CLINES BEGIN
				
				ZAXIS       "Zloc"              0.00000      0.00000
				YAXIS       "Yloc"              0.00000     90.00000
				
				PARALLEL    "L4"           "Offset"       NEG  LINE   "Yloc"
				PARALLEL    "L1"                0.50000   NEG  LINE   "L4"
				PARALLEL    "L2"           "Height"       POS  LINE   "Zloc"
				PARALLEL    "L3"           "Bottom"       NEG  LINE   "Zloc"
				
			CLINES END
			
			CBOUNDARIES BEGIN
				
				BOUNDARY "Boundary 1" BEGIN
					
					POINTS BEGIN
						
						BPOINT       1  LSECT   "L2"    "L4"
						BPOINT       2  LSECT   "L4"    "L3"
						BPOINT       3  LSECT   "L1"    "L3"
						BPOINT       4  LSECT   "L1"    "L2"
						
					POINTS END
					
				BOUNDARY END
				
			CBOUNDARIES END
			
			CUNITS BEGIN
				
				SBEAM       1    LSECT     "L4"      "L3"
				
				SBEAM       1    BOUNDARY  "Boundary 1"
				
			CUNITS END
			
			CPROPSETS 1 BEGIN
				
				PROPERTY    IFC            OBJTYPE        "IfcWall:PARAPET"
				PROPERTY    IFC            OBJNAME        "Parapet wall"
				
			CPROPSETS END
			
		CSECTION END
		
		CSECTION "Wingwall with foundation" BEGIN
			
			TEXT   ""
			
			CVARS BEGIN
				
				VAR         "Offset"                   0.00000  LENGTH  ""
				VAR         "Height"                   5.00000  LENGTH  ""
				
			CVARS END
			
			CLINES BEGIN
				
				ZAXIS       "Zloc"              0.00000      0.00000
				YAXIS       "Yloc"              0.00000     90.00000
				
				PARALLEL    "L7"           "Offset"       NEG  LINE   "Yloc"
				PARALLEL    "L1"                0.50000   NEG  LINE   "L7"
				PARALLEL    "L2"           "Height"       POS  LINE   "Zloc"
				PARALLEL    "L4"                1.00000   NEG  LINE   "Zloc"
				PARALLEL    "L5"                1.00000   NEG  LINE   "L1"
				PARALLEL    "L6"                1.00000   POS  LINE   "L7"
				
			CLINES END
			
			CBOUNDARIES BEGIN
				
				BOUNDARY "Boundary 1" BEGIN
					
					POINTS BEGIN
						
						BPOINT       1  LSECT   "L2"    "L7"
						BPOINT       2  LSECT   "L7"    "Zloc"
						BPOINT       3  LSECT   "L1"    "Zloc"
						BPOINT       4  LSECT   "L1"    "L2"
						
					POINTS END
					
				BOUNDARY END
				
				BOUNDARY "Boundary 2" BEGIN
					
					POINTS BEGIN
						
						BPOINT       1  LSECT   "L6"    "Zloc"
						BPOINT       2  LSECT   "L4"    "L6"
						BPOINT       3  LSECT   "L4"    "L5"
						BPOINT       4  LSECT   "L5"    "Zloc"
						
					POINTS END
					
				BOUNDARY END
				
			CBOUNDARIES END
			
			CUNITS BEGIN
				
				SBEAM       2    LSECT     "L7"      "Zloc"
				SBEAM       1    LSECT     "Zloc"    "Yloc"
				
				SBEAM       2    BOUNDARY  "Boundary 2"
				SBEAM       1    BOUNDARY  "Boundary 1"
				
			CUNITS END
			
			CPROPSETS 2 BEGIN
				
				PROPERTY    IFC            OBJTYPE        "IfcFooting:PAD_FOOTING"
				PROPERTY    IFC            OBJNAME        "Footing"
				
			CPROPSETS END
			
			CPROPSETS 1 BEGIN
				
				PROPERTY    IFC            OBJTYPE        "IfcWall:PARAPET"
				PROPERTY    IFC            OBJNAME        "Parapet wall"
				
			CPROPSETS END
			
		CSECTION END
		
		CSECTION "Foundation 1" BEGIN
			
			TEXT   ""
			
			CVARS BEGIN
				
			CVARS END
			
			CLINES BEGIN
				
				ZAXIS       "Zloc"              0.00000      0.00000
				YAXIS       "Yloc"              0.00000     90.00000
				
				ABSANGLE    "L1"              -60.00000        LSECT  "Zloc" "Yloc"
				ABSANGLE    "L2"                5.00000        LSECT  "Zloc" "Yloc"
				PARALLEL    "L3"                2.00000   NEG  LINE   "Zloc"
				PARALLEL    "L4"                0.50000   NEG  LINE   "Yloc"
				PARALLEL    "L5"                2.00000   POS  LINE   "Yloc"
				
			CLINES END
			
			CBOUNDARIES BEGIN
				
				BOUNDARY "Boundary 1" BEGIN
					
					POINTS BEGIN
						
						BPOINT       1  LSECT   "Zloc"  "Yloc"
						BPOINT       2  LSECT   "L4"    "L1"
						BPOINT       3  LSECT   "L3"    "L4"
						BPOINT       4  LSECT   "L3"    "L5"
						BPOINT       5  LSECT   "L5"    "L2"
						
					POINTS END
					
				BOUNDARY END
				
			CBOUNDARIES END
			
			CUNITS BEGIN
				
				SBEAM       1    LSECT     "Zloc"    "Yloc"
				
				SBEAM       1    BOUNDARY  "Boundary 1"
				
			CUNITS END
			
			CPROPSETS 1 BEGIN
				
				PROPERTY    IFC            OBJTYPE        "IfcFooting:FOOTING_BEAM"
				PROPERTY    IFC            OBJNAME        "Foundation 1"
				
			CPROPSETS END
			
		CSECTION END
		
		CSECTION "Foundation 2" BEGIN
			
			TEXT   ""
			
			CVARS BEGIN
				
			CVARS END
			
			CLINES BEGIN
				
				ZAXIS       "Zloc"              0.00000      0.00000
				YAXIS       "Yloc"              0.00000     90.00000
				
				ABSANGLE    "L1"               60.00000        LSECT  "Zloc" "Yloc"
				ABSANGLE    "L2"               -5.00000        LSECT  "Zloc" "Yloc"
				PARALLEL    "L3"                2.00000   NEG  LINE   "Zloc"
				PARALLEL    "L4"                0.50000   POS  LINE   "Yloc"
				PARALLEL    "L5"                2.00000   NEG  LINE   "Yloc"
				
			CLINES END
			
			CBOUNDARIES BEGIN
				
				BOUNDARY "Boundary 1" BEGIN
					
					POINTS BEGIN
						
						BPOINT       1  LSECT   "Zloc"  "Yloc"
						BPOINT       2  LSECT   "L4"    "L1"
						BPOINT       3  LSECT   "L3"    "L4"
						BPOINT       4  LSECT   "L3"    "L5"
						BPOINT       5  LSECT   "L5"    "L2"
						
					POINTS END
					
				BOUNDARY END
				
			CBOUNDARIES END
			
			CUNITS BEGIN
				
				SBEAM       1    LSECT     "Zloc"    "Yloc"
				
				SBEAM       1    BOUNDARY  "Boundary 1"
				
			CUNITS END
			
			CPROPSETS 1 BEGIN
				
				PROPERTY    IFC            OBJTYPE        "IfcFooting:FOOTING_BEAM"
				PROPERTY    IFC            OBJNAME        "Foundation 2"
				
			CPROPSETS END
			
		CSECTION END
		
	CSECTIONS END
	
	#---------------------------------------------------------------------------
	# Model structure
	#---------------------------------------------------------------------------
	
	STRUCTURE BEGIN
		
		GIRDER "Bridge" BEGIN
			
			TEXT            ""
			IFC  OBJTYPE    "IfcBridgePart:DECK"
			REFAXIS         "Axis"
			CSPLANE         NORMAL
			SBEGIN                 0.000000
			
			STATIONS BEGIN
				
				SGLOBAL s001           0.000000    BEAM
				SGLOBAL s002           2.500000    BEAM
				SGLOBAL s003           5.000000    BEAM
				SGLOBAL s004           7.500000    BEAM
				SGLOBAL s005          10.000000    BEAM
				SGLOBAL s006          12.500000    BEAM
				SGLOBAL s007          15.000000    BEAM
				SGLOBAL s008          17.500000    BEAM
				SGLOBAL s009          20.000000    BEAM
				SGLOBAL s010          22.500000    BEAM
				SGLOBAL s011          25.000000    BEAM
				SGLOBAL s012          27.500000    BEAM
				SGLOBAL s013          30.000000    BEAM
				SGLOBAL s014          32.500000    BEAM
				SGLOBAL s015          35.000000    BEAM
				SGLOBAL s016          37.500000    BEAM
				SGLOBAL s017          40.000000    BEAM
				SGLOBAL s018          42.500000    BEAM
				SGLOBAL s019          45.000000    BEAM
				SGLOBAL s020          47.500000    BEAM
				SGLOBAL s021          50.000000    BEAM
				
			STATIONS END
			
			SPOINT            s001              CSECTION   "" "Bridge"
			SPOINT      [XFTS s002   s020   1]  CSECTION   "Bridge"
			SPOINT            s021              CSECTION   "Bridge" ""
			
			SPOINT      [XFTS s001   s021   1]  ZROTATE    0.00000
			
			SPOINT      [XFTS s001   s021   1]  YROTATE    0.00000
			
			SPOINT            s001              VARIABLE   "RefL"       ""                      "cd2ax_SecondaryAxis_1(0.0,0.0)"
			SPOINT      [XFTS s002   s020   1]  VARIABLE   "RefL"       "cd2ax_SecondaryAxis_1(0.0,0.0)"
			SPOINT            s021              VARIABLE   "RefL"       "cd2ax_SecondaryAxis_1(0.0,0.0)" ""
			SPOINT            s001              VARIABLE   "RefR"       ""                      "cd2ax_SecondaryAxis_2(0.0,0.0)"
			SPOINT      [XFTS s002   s020   1]  VARIABLE   "RefR"       "cd2ax_SecondaryAxis_2(0.0,0.0)"
			SPOINT            s021              VARIABLE   "RefR"       "cd2ax_SecondaryAxis_2(0.0,0.0)" ""
			
			SPOINT      [XFTS s001   s021   1]  NODE       "1"               0   STEP     0
			
			SPOINT      [XFTS s001   s020   1]  BEAM       "1"               0   STEP     0
			
			SPOINT      [XFTS s001   s020   1]  MATERIAL   "1"          "EN:C35/45"
			
			SPOINT      [XFTS s001   s020   1]  GROUP      "1"          ""
			
			GRILLAGE "OFF" BEGIN
				
				MATERIAL         ""
				GROUP            ""
				CSECTION         ""                0.00000
				ELEMS                 0      0
				
			GRILLAGE END
			
		GIRDER END
		
		GIRDER "Wingwall L" BEGIN
			
			TEXT            ""
			IFC  OBJTYPE    "IfcBridgePart:SUPERSTRUCTURE"
			REFAXIS         "SecondaryAxis_1"
			CSPLANE         NORMAL
			SBEGIN                 0.000000
			
			STATIONS BEGIN
				
				SGLOBAL s001          23.236500    BEAM
				SGLOBAL s002          25.736500    BEAM
				SGLOBAL s003          28.236500    BEAM
				SGLOBAL s004          30.736500    BEAM
				SGLOBAL s005          32.236500    BEAM
				SGLOBAL s006          33.236500    BEAM
				SGLOBAL s007          35.736500    BEAM
				SGLOBAL s008          38.236500    BEAM
				SGLOBAL s009          40.736500    BEAM
				SGLOBAL s010          43.236500    BEAM
				SGLOBAL s011          45.736500    BEAM
				SGLOBAL s012          48.236500    BEAM
				SGLOBAL s013          50.736500    BEAM
				SGLOBAL s014          53.236500    BEAM
				SGLOBAL s015          55.736500    BEAM
				SGLOBAL s016          58.236500    BEAM
				SGLOBAL s017          60.736500    BEAM
				SGLOBAL s018          63.236500    BEAM
				SGLOBAL s019          65.736500    BEAM
				SGLOBAL s020          68.236500    BEAM
				SGLOBAL s021          70.736500    BEAM
				SGLOBAL s022          73.236500    BEAM
				SGLOBAL s023          75.736500    BEAM
				SGLOBAL s024          78.236500    BEAM
				SGLOBAL s025          80.736500    BEAM
				SGLOBAL s026          83.236500    BEAM
				SGLOBAL s027          84.236500    BEAM
				SGLOBAL s028          85.736500    BEAM
				SGLOBAL s029          88.236500    BEAM
				SGLOBAL s030          90.736500    BEAM
				SGLOBAL s031          93.236500    BEAM
				
			STATIONS END
			
			SPOINT            s001              CSECTION   "" "Wingwall with foundation"
			SPOINT      [XFTS s002   s004   1]  CSECTION   "Wingwall with foundation"
			SPOINT            s005              CSECTION   "Wingwall with foundation" "Wingwall"
			SPOINT      [XFTS s006   s026   1]  CSECTION   "Wingwall"
			SPOINT            s027              CSECTION   "Wingwall" "Wingwall with foundation"
			SPOINT      [XFTS s028   s030   1]  CSECTION   "Wingwall with foundation"
			SPOINT            s031              CSECTION   "Wingwall with foundation" ""
			
			SPOINT      [XFTS s001   s031   1]  ZROTATE    0.00000
			
			SPOINT      [XFTS s001   s031   1]  YROTATE    0.00000
			
			SPOINT            s005              VARIABLE   "Bottom"     ""                      "cdh2ax_Axis(1.0,0.0)"
			SPOINT      [XFTS s006   s026   1]  VARIABLE   "Bottom"     "cdh2ax_Axis(1.0,0.0)"
			SPOINT            s027              VARIABLE   "Bottom"     "cdh2ax_Axis(1.0,0.0)"  ""
			SPOINT            s001              VARIABLE   "Height"     ""                      "Height(\$s)"
			SPOINT      [XFTS s002   s030   1]  VARIABLE   "Height"     "Height(\$s)"
			SPOINT            s031              VARIABLE   "Height"     "Height(\$s)"           ""
			
			SPOINT      [XFTS s001   s031   1]  NODE       "1"               0   STEP     0
			SPOINT      [XFTS s001   s031   1]  NODE       "2"               0   STEP     0
			
			SPOINT      [XFTS s001   s030   1]  BEAM       "1"               0   STEP     0
			SPOINT      [XFTS s001   s030   1]  BEAM       "2"               0   STEP     0
			
			SPOINT      [XFTS s001   s030   1]  MATERIAL   "1"          "EN:C35/45"
			SPOINT      [XFTS s001   s004   1]  MATERIAL   "2"          "EN:C35/45"
			SPOINT      [XFTS s005   s026   1]  MATERIAL   "2"          ""
			SPOINT      [XFTS s027   s030   1]  MATERIAL   "2"          "EN:C35/45"
			
			SPOINT      [XFTS s001   s030   1]  GROUP      "1"          ""
			SPOINT      [XFTS s001   s030   1]  GROUP      "2"          ""
			
			GRILLAGE "OFF" BEGIN
				
				MATERIAL         ""
				GROUP            ""
				CSECTION         ""                0.00000
				ELEMS                 0      0
				
			GRILLAGE END
			
		GIRDER END
		
		GIRDER "Wingwall R" BEGIN
			
			TEXT            ""
			IFC  OBJTYPE    "IfcBridgePart:SUPERSTRUCTURE"
			REFAXIS         "SecondaryAxis_2"
			CSPLANE         NORMAL
			SBEGIN                 0.000000
			
			STATIONS BEGIN
				
				SGLOBAL s001          23.236500    BEAM
				SGLOBAL s002          25.736500    BEAM
				SGLOBAL s003          28.236500    BEAM
				SGLOBAL s004          30.736500    BEAM
				SGLOBAL s005          32.236500    BEAM
				SGLOBAL s006          33.236500    BEAM
				SGLOBAL s007          35.736500    BEAM
				SGLOBAL s008          38.236500    BEAM
				SGLOBAL s009          40.736500    BEAM
				SGLOBAL s010          43.236500    BEAM
				SGLOBAL s011          45.736500    BEAM
				SGLOBAL s012          48.236500    BEAM
				SGLOBAL s013          50.736500    BEAM
				SGLOBAL s014          53.236500    BEAM
				SGLOBAL s015          55.736500    BEAM
				SGLOBAL s016          58.236500    BEAM
				SGLOBAL s017          60.736500    BEAM
				SGLOBAL s018          63.236500    BEAM
				SGLOBAL s019          65.736500    BEAM
				SGLOBAL s020          68.236500    BEAM
				SGLOBAL s021          70.736500    BEAM
				SGLOBAL s022          73.236500    BEAM
				SGLOBAL s023          75.736500    BEAM
				SGLOBAL s024          78.236500    BEAM
				SGLOBAL s025          80.736500    BEAM
				SGLOBAL s026          83.236500    BEAM
				SGLOBAL s027          84.236500    BEAM
				SGLOBAL s028          85.736500    BEAM
				SGLOBAL s029          88.236500    BEAM
				SGLOBAL s030          93.236500    BEAM
				
			STATIONS END
			
			SPOINT            s001              CSECTION   "" "Wingwall with foundation"
			SPOINT      [XFTS s002   s004   1]  CSECTION   "Wingwall with foundation"
			SPOINT            s005              CSECTION   "Wingwall with foundation" "Wingwall"
			SPOINT      [XFTS s006   s026   1]  CSECTION   "Wingwall"
			SPOINT            s027              CSECTION   "Wingwall" "Wingwall with foundation"
			SPOINT      [XFTS s028   s029   1]  CSECTION   "Wingwall with foundation"
			SPOINT            s030              CSECTION   "Wingwall with foundation" ""
			
			SPOINT      [XFTS s001   s030   1]  ZROTATE    0.00000
			
			SPOINT      [XFTS s001   s030   1]  YROTATE    0.00000
			
			SPOINT            s005              VARIABLE   "Bottom"     ""                      "cdh2ax_Axis(1.0,0.0)"
			SPOINT      [XFTS s006   s026   1]  VARIABLE   "Bottom"     "cdh2ax_Axis(1.0,0.0)"
			SPOINT            s027              VARIABLE   "Bottom"     "cdh2ax_Axis(1.0,0.0)"  ""
			SPOINT            s001              VARIABLE   "Height"     ""                      "Height(\$s)"
			SPOINT      [XFTS s002   s029   1]  VARIABLE   "Height"     "Height(\$s)"
			SPOINT            s030              VARIABLE   "Height"     "Height(\$s)"           ""
			SPOINT            s001              VARIABLE   "Offset"     ""                      "-0.5"
			SPOINT      [XFTS s002   s029   1]  VARIABLE   "Offset"     "-0.5"
			SPOINT            s030              VARIABLE   "Offset"     "-0.5"                  ""
			
			SPOINT      [XFTS s001   s030   1]  NODE       "1"               0   STEP     0
			SPOINT      [XFTS s001   s030   1]  NODE       "2"               0   STEP     0
			
			SPOINT      [XFTS s001   s029   1]  BEAM       "1"               0   STEP     0
			SPOINT      [XFTS s001   s029   1]  BEAM       "2"               0   STEP     0
			
			SPOINT      [XFTS s001   s029   1]  MATERIAL   "1"          "EN:C35/45"
			SPOINT      [XFTS s001   s004   1]  MATERIAL   "2"          "EN:C35/45"
			SPOINT      [XFTS s005   s026   1]  MATERIAL   "2"          ""
			SPOINT      [XFTS s027   s029   1]  MATERIAL   "2"          "EN:C35/45"
			
			SPOINT      [XFTS s001   s029   1]  GROUP      "1"          ""
			SPOINT      [XFTS s001   s029   1]  GROUP      "2"          ""
			
			GRILLAGE "OFF" BEGIN
				
				MATERIAL         ""
				GROUP            ""
				CSECTION         ""                0.00000
				ELEMS                 0      0
				
			GRILLAGE END
			
		GIRDER END
		
		GIRDER "Foundation 1" BEGIN
			
			TEXT            ""
			IFC  OBJTYPE    "IfcBridgePart:SUBSTRUCTURE"
			REFAXIS         "Trans Axis 1"
			CSPLANE         NORMAL
			SBEGIN                 0.000000
			
			STATIONS BEGIN
				
				SGLOBAL s001         -20.000000    BEAM
				SGLOBAL s002         -15.000000    BEAM
				SGLOBAL s003         -10.000000    BEAM
				SGLOBAL s004          -5.000000    BEAM
				SGLOBAL s005           0.000000    BEAM
				SGLOBAL s006           5.000000    BEAM
				SGLOBAL s007          10.000000    BEAM
				SGLOBAL s008          15.000000    BEAM
				SGLOBAL s009          20.000000    BEAM
				
			STATIONS END
			
			SPOINT            s001              CSECTION   "" "Foundation 1"
			SPOINT      [XFTS s002   s008   1]  CSECTION   "Foundation 1"
			SPOINT            s009              CSECTION   "Foundation 1" ""
			
			SPOINT      [XFTS s001   s009   1]  ZROTATE    0.00000
			
			SPOINT      [XFTS s001   s009   1]  YROTATE    0.00000
			
			
			SPOINT      [XFTS s001   s009   1]  NODE       "1"               0   STEP     0
			
			SPOINT      [XFTS s001   s008   1]  BEAM       "1"               0   STEP     0
			
			SPOINT      [XFTS s001   s008   1]  MATERIAL   "1"          "EN:C35/45"
			
			SPOINT      [XFTS s001   s008   1]  GROUP      "1"          ""
			
			GRILLAGE "OFF" BEGIN
				
				MATERIAL         ""
				GROUP            ""
				CSECTION         ""                0.00000
				ELEMS                 0      0
				
			GRILLAGE END
			
		GIRDER END
		
		GIRDER "Foundation 2" BEGIN
			
			TEXT            ""
			IFC  OBJTYPE    "IfcBridgePart:SUBSTRUCTURE"
			REFAXIS         "Trans Axis 2"
			CSPLANE         NORMAL
			SBEGIN                 0.000000
			
			STATIONS BEGIN
				
				SGLOBAL s001         -20.000000    BEAM
				SGLOBAL s002         -15.000000    BEAM
				SGLOBAL s003         -10.000000    BEAM
				SGLOBAL s004          -5.000000    BEAM
				SGLOBAL s005           0.000000    BEAM
				SGLOBAL s006           5.000000    BEAM
				SGLOBAL s007          10.000000    BEAM
				SGLOBAL s008          15.000000    BEAM
				SGLOBAL s009          20.000000    BEAM
				
			STATIONS END
			
			SPOINT            s001              CSECTION   "" "Foundation 2"
			SPOINT      [XFTS s002   s008   1]  CSECTION   "Foundation 2"
			SPOINT            s009              CSECTION   "Foundation 2" ""
			
			SPOINT      [XFTS s001   s009   1]  ZROTATE    0.00000
			
			SPOINT      [XFTS s001   s009   1]  YROTATE    0.00000
			
			
			SPOINT      [XFTS s001   s009   1]  NODE       "1"               0   STEP     0
			
			SPOINT      [XFTS s001   s008   1]  BEAM       "1"               0   STEP     0
			
			SPOINT      [XFTS s001   s008   1]  MATERIAL   "1"          "EN:C35/45"
			
			SPOINT      [XFTS s001   s008   1]  GROUP      "1"          ""
			
			GRILLAGE "OFF" BEGIN
				
				MATERIAL         ""
				GROUP            ""
				CSECTION         ""                0.00000
				ELEMS                 0      0
				
			GRILLAGE END
			
		GIRDER END
		
		#-----------------------------------------------------------------------
		# Geometrical positions of structural members
		#-----------------------------------------------------------------------
		
		GPOSITIONS BEGIN
			
		GPOSITIONS END
		
		#-----------------------------------------------------------------------
		# Topological connections of structural members (Analysis)
		#-----------------------------------------------------------------------
		
		CONNECTIONS BEGIN
			
			
		CONNECTIONS END
		
	STRUCTURE END
	
	#---------------------------------------------------------------------------
	# Construction
	#---------------------------------------------------------------------------
	
	CONSTRUCTION "Construction" BEGIN
		
		TEXT       ""
		DAYBEGIN   1
		OPTION     CALCULATION       ON
		
		PHASE "Phase 1" BEGIN
			
			TEXT       ""
			DAYBEGIN   1
			
			ASSEMBLIES BEGIN
				
				ASM        1  MEMBER    "Foundation 1" BEAM  *   SGLOBAL   *              SGLOBAL   *
				ASM        1  MEMBER    "Foundation 2" BEAM  *   SGLOBAL   *              SGLOBAL   *
				
			ASSEMBLIES END
			
			TASKS BEGIN
				
				#task   taskname          day1     duration assembly [SKIP] additional args
				TASK    CONCRETE             1 LOCAL     28     1           "Dshrink=0" "descr=Concrete (pour + curing)"
				
			TASKS END
			
		PHASE END
		
		PHASE "Phase 2" BEGIN
			
			TEXT       ""
			DAYBEGIN   28
			
			ASSEMBLIES BEGIN
				
				ASM        1  MEMBER    "Bridge"      BEAM  *    SGLOBAL   *              SGLOBAL   *
				
			ASSEMBLIES END
			
			TASKS BEGIN
				
				#task   taskname          day1     duration assembly [SKIP] additional args
				TASK    CONCRETE             1 LOCAL     28     1           "Dshrink=0" "descr=Concrete (pour + curing)"
				
			TASKS END
			
		PHASE END
		
		PHASE "Phase 3" BEGIN
			
			TEXT       ""
			DAYBEGIN   28
			
			ASSEMBLIES BEGIN
				
				ASM        1  MEMBER    "Wingwall R"  BEAM  2    SGLOBAL   *              SGLOBAL   *
				ASM        1  MEMBER    "Wingwall L"  BEAM  2    SGLOBAL   *              SGLOBAL   *
				
			ASSEMBLIES END
			
			TASKS BEGIN
				
				#task   taskname          day1     duration assembly [SKIP] additional args
				TASK    CONCRETE             1 LOCAL     28     1           "Dshrink=0" "descr=Concrete (pour + curing)"
				
			TASKS END
			
		PHASE END
		
		PHASE "Phase 4" BEGIN
			
			TEXT       ""
			DAYBEGIN   56
			
			ASSEMBLIES BEGIN
				
				ASM        1  MEMBER    "Wingwall R"  BEAM  1    SGLOBAL   *              SGLOBAL   *
				ASM        1  MEMBER    "Wingwall L"  BEAM  1    SGLOBAL   *              SGLOBAL   *
				
			ASSEMBLIES END
			
			TASKS BEGIN
				
				#task   taskname          day1     duration assembly [SKIP] additional args
				TASK    CONCRETE             1 LOCAL     28     1           "Dshrink=0" "descr=Concrete (pour + curing)"
				
			TASKS END
			
		PHASE END
		
	CONSTRUCTION END
	
ABM END
