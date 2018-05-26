# utl_slopegarphs_and_5_10_15_20_year_survival_rates
Slopegarphs and 5 10 15 20 year cancel survival rates. Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.

    Slopegarphs and 5 10 15 20 year cancel survival rates

    A SAS ODS Graphics "remix" of Edward Tufte's cancer survival

    github
    https://github.com/rogerjdeangelis/utl_slopegarphs_and_5_10_15_20_year_survival_rates

    see SAS Forum
    https://tinyurl.com/y7on246y
    https://communities.sas.com/t5/SAS-GRAPH-and-ODS-Graphics/A-SAS-ODS-Graphics-quot-remix-quot-of-Edward-Tufte-s-cancer/m-p/465280


    INPUT
    =====

     WORK.RATES total obs=24

      CANCER_TYPE              _5_YEAR    _10_YEAR    _15_YEAR    _20_YEAR

      Prostate                    99         95          87          81
      Thyroid                     96         96          94          95
      Testis                      95         94          91          88
      Melanomas                   89         87          84          83
      Breast                      86         78          71          65
      Hodgkin's disease           85         80          74          67
      Corpus uteri, uterus        84         83          81          79
      Urinary, bladder            82         76          70          68
      Cervix, uteri               71         64          63          60
      Larynx                      69         57          46          38
      Rectum                      63         55          52          49
      Kidney, renal pelvis        62         54          50          47
      Colon                       62         55          54          52
      Non-Hodgkin's               58         46          38          34
      Oral cavity, pharynx        57         44          38          33
      Ovary                       55         49          50          50
      Leukemia                    43         32          30          26
      Brain, nervous system       32         29          28          26
      Multiple myeloma            30         13           7           5
      Stomach                     24         19          19          15
      Lung and bronchus           15         11           8           6
      Esophagus                   14          8           8           5
      Liver, bile duct             8          6           6           8
      Pancreas                     4          3           3           3


    PROCESS
    =======

    /* Create 11"x17" slopegraph */
    ods pdf file="d:/pdf/&pgm..pdf";
    ods graphics / width=11in height=17in antialias;

    proc sgplot data=ratLon noautolegend noborder;

    title height=12pt "Estimates of relative survival rates, by cancer site";

    /* Repeat SERIES statement twice to get labels at beginning and end of series lines */

    series x=year y=rate / group=cancer_type curvelabelpos=min curvelabel curvelabelloc=outside
      curvelabelattrs=(size=8pt color=black weight=bold) lineattrs=(pattern=solid thickness=1.5pt);

    series x=year y=rate / group=cancer_type curvelabelpos=max curvelabel curvelabelloc=outside
      curvelabelattrs=(size=8pt color=black weight=bold) lineattrs=(pattern=solid thickness=1.5pt);

    /* Create whitespace surrounding rates */
    text x=year y=rate text=rate / strip textattrs=(size=8pt color=black weight=bold)
       backlight=0 backfill fillattrs=(color=white);  /* Create whitespace surrounding rates */
    text x=year y=rate text=rate / strip textattrs=(size=8pt color=black weight=bold);

    /* Repeat a second time without backfill to ensure rates aren't obscured by whitespace */
    xaxis display=none type=discrete; yaxis display=none;

    /* Look Ma, no axes! */
    refline 5 10 15 20 / axis=x label=('5 year' '10 year' '15 year' '20 year')
       labelattrs=(size=8pt color=black weight=bold) lineattrs=(thickness=0pt)
       labelloc=outside; /* Headings */

    footnote height=8pt italic "Based on Edward Tufte discussion group thread at https://tinyurl.com/yb8l9xoq";
    footnote2 height=8pt italic "Data sourced from https://github.com/pascal-schetelat/Slope";

    run;quit;
    ods pdf close;


    OUTPUT
    ======

     Percent of Patients Tha Survived for 5, 10, 20 an 25 Years by Cancer Type


    Survival Percent of Patients
         --+-----------------+-----------------+-----------------+--
      50 +                                                         +
         |                                                         |
         |                                                         |
         |                                                         |
         |                                                         |
         | * 5yr Leukemia                                          |
         |    *                                                    |
      40 +       *                                                 +
         |                                                         |
         |          *                                              |
         |             *                                           |
         |                                                         |
         |                *                                        |
         |                   * 10yr * * * * * *                    |
      30 +                                     * 15yr              +
         |                                      \                  |
         |                                       \                 |
         |                                         20yr Leukemia   |
         | * 5yr Stomach                                           |
         |    *                                                    |
         |         *                                               |
      20 +              *                                          +
         |                   * 10yr * * * * * *                    |
         |                                      * 15yr             |
         |                                       \                 |
         |                                        \ 20yr Stomach * |
         |                                                         |
         |                                                         |
      10 +                                                         +
         --+-----------------+-----------------+-----------------+--
           5                10                15                20

                                    YEAR

    *                _              _       _
     _ __ ___   __ _| | _____    __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|

    ;
    data _null_;
    file "d:/csv/utl_slopegarphs_and_5_10_15_20_year_survival_rates.csv";
    input;
    put _infile_;
    cards4;
    Cancer type,5 year,10 year,15 year,20 year
    Prostate,99,95,87,81
    Thyroid,96,96,94,95
    Testis,95,94,91,88
    Melanomas,89,87,84,83
    Breast,86,78,71,65
    Hodgkin's disease,85,80,74,67
    "Corpus uteri, uterus",84,83,81,79
    "Urinary, bladder",82,76,70,68
    "Cervix, uteri",71,64,63,60
    Larynx,69,57,46,38
    Rectum,63,55,52,49
    "Kidney, renal pelvis",62,54,50,47
    Colon,62,55,54,52
    Non-Hodgkin's,58,46,38,34
    "Oral cavity, pharynx",57,44,38,33
    Ovary,55,49,50,50
    Leukemia,43,32,30,26
    "Brain, nervous system",32,29,28,26
    Multiple myeloma,30,13,7,5
    Stomach,24,19,19,15
    Lung and bronchus,15,11,8,6
    Esophagus,14,8,8,5
    "Liver, bile duct",8,6,6,8
    Pancreas,4,3,3,3
    ;;;;
    run;quit;

    * inport the data;
    dm "dimport 'd:/csv/utl_slopegarphs_and_5_10_15_20_year_survival_rates.csv' work.rates replace";
    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;
    * normalize;
    data ratLon;

      set rates;

      rate =  _5_year ; year =  5 ; output ;
      rate = _10_year ; year = 10 ; output ;
      rate = _15_year ; year = 15 ; output ;
      rate = _20_year ; year = 20 ; output ;

      keep cancer_type rate year;

    run;quit;



    /* Create 11"x17" slopegraph */
    ods pdf file="d:/pdf/utl_slopegarphs_and_5_10_15_20_year_survival_rates.pdf";
    ods graphics / width=11in height=17in antialias;

    proc sgplot data=ratLon noautolegend noborder;

    title height=12pt "Estimates of relative survival rates, by cancer site";

    /* Repeat SERIES statement twice to get labels at beginning and end of series lines */

    series x=year y=rate / group=cancer_type curvelabelpos=min curvelabel curvelabelloc=outside
      curvelabelattrs=(size=8pt color=black weight=bold) lineattrs=(pattern=solid thickness=1.5pt);

    series x=year y=rate / group=cancer_type curvelabelpos=max curvelabel curvelabelloc=outside
      curvelabelattrs=(size=8pt color=black weight=bold) lineattrs=(pattern=solid thickness=1.5pt);

    /* Create whitespace surrounding rates */
    text x=year y=rate text=rate / strip textattrs=(size=8pt color=black weight=bold)
       backlight=0 backfill fillattrs=(color=white);  /* Create whitespace surrounding rates */
    text x=year y=rate text=rate / strip textattrs=(size=8pt color=black weight=bold);

    /* Repeat a second time without backfill to ensure rates aren't obscured by whitespace */
    xaxis display=none type=discrete; yaxis display=none;

    /* Look Ma, no axes! */
    refline 5 10 15 20 / axis=x label=('5 year' '10 year' '15 year' '20 year')
       labelattrs=(size=8pt color=black weight=bold) lineattrs=(thickness=0pt)
       labelloc=outside; /* Headings */

    footnote height=8pt italic "Based on Edward Tufte discussion group thread at https://tinyurl.com/yb8l9xoq";
    footnote2 height=8pt italic "Data sourced from https://github.com/pascal-schetelat/Slope";

    run;quit;
    ods pdf close;

    *           _       _           _       _
     _ __  _ __(_)_ __ | |_   _ __ | | ___ | |_
    | '_ \| '__| | '_ \| __| | '_ \| |/ _ \| __|
    | |_) | |  | | | | | |_  | |_) | | (_) | |_
    | .__/|_|  |_|_| |_|\__| | .__/|_|\___/ \__|
    |_|                      |_|
    ;

    * you need to use the excelent classic program editor graphics editor

    data ratLonFix;
      set ratlon;
      select (year);
        when (5,20) lbl=catx(' ',cats(put(year,2.),'yr'),cancer_type);
        otherwise lbl=cats(put(year,2.),'yr');
      end;
    run;quit;

    options ls=64 ps=40;
    proc plot data=ratLonFix(where=(cancer_type in ('Leukemia','Stomach'))) ;
     plot rate*year='*' $  lbl /haxis=5 10 15 20  box;
    run;quit;
    options ls=171 ps=66;


