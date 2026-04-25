# Schema Relation Growth Report

## Inputs And Assumptions

- `|R_case|` is counted from `canon_schema_case*.json` -> `relation_types`.
- Initial schema is treated as empty for each case.
- A relation event is `new` the first time its raw relation appears in that case.
- Later occurrences of the same raw relation are `reused` because the relation is already in the growing schema.
- Growth curves use cumulative unique raw relations by sample index from `case*.json`.
- `schema_only_relation_count` is `relation_count - final_cumulative_relations`; it captures final-schema relations not observed as raw relation events in `case*.json`.

## Summary By Case

| iter | case | relation_count | relation_event_count | new_relation_event_count | reused_relation_event_count | new_relation_event_ratio | reused_relation_event_ratio | final_cumulative_relations | schema_only_relation_count | max_new_relations_at_idx | max_growth_idx |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| iter0 | case1_name_only | 514 | 3753 | 511 | 3242 | 0.1362 | 0.8638 | 511 | 3 | 6 | 1 |
| iter0 | case2_name_general | 502 | 3753 | 502 | 3251 | 0.1338 | 0.8662 | 502 | 0 | 6 | 1 |
| iter0 | case3_name_detail | 528 | 3753 | 527 | 3226 | 0.1404 | 0.8596 | 527 | 1 | 6 | 1 |
| iter0 | case4_detail_strict | 487 | 3753 | 484 | 3269 | 0.1290 | 0.8710 | 484 | 3 | 6 | 1 |
| iter0 | case5_concat | 496 | 3753 | 493 | 3260 | 0.1314 | 0.8686 | 493 | 3 | 6 | 1 |
| iter0 | case6_weighted | 558 | 3753 | 555 | 3198 | 0.1479 | 0.8521 | 555 | 3 | 6 | 1 |


## Ranking: Largest Final Schema

| case | relation_count | final_cumulative_relations | schema_only_relation_count |
| --- | --- | --- | --- |
| case6_weighted | 558 | 555 | 3 |
| case3_name_detail | 528 | 527 | 1 |
| case1_name_only | 514 | 511 | 3 |
| case2_name_general | 502 | 502 | 0 |
| case5_concat | 496 | 493 | 3 |
| case4_detail_strict | 487 | 484 | 3 |


## Ranking: Highest New Relation Event Ratio

| case | new_relation_event_ratio | new_relation_event_count | relation_event_count |
| --- | --- | --- | --- |
| case6_weighted | 0.1479 | 555 | 3753 |
| case3_name_detail | 0.1404 | 527 | 3753 |
| case1_name_only | 0.1362 | 511 | 3753 |
| case2_name_general | 0.1338 | 502 | 3753 |
| case5_concat | 0.1314 | 493 | 3753 |
| case4_detail_strict | 0.1290 | 484 | 3753 |


## Growth Curve

![Combined growth curve](schema_growth_curve.svg)

## Largest Growth Bursts

| case | idx | new_relations_at_idx | cumulative_relations | new_relation_names |
| --- | --- | --- | --- | --- |
| case1_name_only | 1 | 6 | 7 | isPartOf; populationDensity; population; utcOffset; governmentType; leaderTitle |
| case1_name_only | 33 | 6 | 72 | discoveredBy; discoveryDate; rotationPeriod; orbitalPeriod; apoapsis; absoluteMagnitude |
| case2_name_general | 1 | 6 | 7 | isPartOf; populationDensity; population; utcOffset; governmentType; leaderTitle |
| case2_name_general | 33 | 6 | 72 | discoveredBy; discoveryDate; rotationPeriod; orbitalPeriod; apoapsis; absoluteMagnitude |
| case3_name_detail | 1 | 6 | 7 | isPartOf; populationDensity; population; utcOffset; governmentType; leaderTitle |
| case3_name_detail | 33 | 6 | 71 | discoveredBy; discoveryDate; rotationPeriod; orbitalPeriod; apoapsis; absoluteMagnitude |
| case4_detail_strict | 1 | 6 | 7 | isPartOf; populationDensity; population; utcOffset; governmentType; leaderTitle |
| case4_detail_strict | 33 | 6 | 71 | discoveredBy; discoveryDate; rotationPeriod; orbitalPeriod; apoapsis; absoluteMagnitude |
| case5_concat | 1 | 6 | 7 | locatedInCountry; populationDensity; population; utcOffset; governmentType; leaderTitle |
| case5_concat | 7 | 6 | 27 | builtIn; municipality; county; type; isPartOf; relateto |
| case5_concat | 33 | 6 | 73 | discoveredBy; discoveryDate; rotationPeriod; orbitalPeriod; apoapsis; absoluteMagnitude |
| case6_weighted | 1 | 6 | 7 | isPartOf; populationDensity; population; utcOffset; governmentType; leaderTitle |
| case6_weighted | 33 | 6 | 73 | discoveredBy; discoveryDate; rotationPeriod; orbitalPeriod; apoapsis; absoluteMagnitude |
| case6_weighted | 871 | 6 | 484 | studentCount; staffCount; studentType; studentCount_Undergraduate; studentCount_Postgraduate; studentCount_Doctoral |
| case1_name_only | 7 | 5 | 26 | builtIn; municipality; county; type; relateto |
| case1_name_only | 154 | 5 | 189 | placeOfBirth; serviceBranch; award; dateOfRetirement; placeOfDeath |
| case2_name_general | 7 | 5 | 26 | builtIn; municipality; county; type; relateto |
| case2_name_general | 154 | 5 | 193 | serviceBranch; awardedTo; award; dateOfRetirement; placeOfDeath |
| case2_name_general | 871 | 5 | 448 | staffCount; studentType; studentCount_Undergraduate; studentCount_Postgraduate; studentCount_Doctoral |
| case3_name_detail | 7 | 5 | 26 | builtIn; municipality; county; type; relateto |
| case3_name_detail | 154 | 5 | 192 | serviceBranch; awardedTo; award; dateOfRetirement; placeOfDeath |
| case3_name_detail | 871 | 5 | 468 | staffCount; studentCount_Undergraduate; studentType; studentCount_Postgraduate; studentCount_Doctoral |
| case4_detail_strict | 7 | 5 | 26 | builtIn; municipality; county; type; relateto |
| case4_detail_strict | 871 | 5 | 425 | staffCount; studentType; studentCount_Undergraduate; studentCount_Postgraduate; studentCount_Doctoral |
| case5_concat | 871 | 5 | 441 | staffCount; studentType; studentCount_Undergraduate; studentCount_Postgraduate; studentCount_Doctoral |
| case6_weighted | 7 | 5 | 26 | builtIn; municipality; county; type; relateto |
| case6_weighted | 28 | 5 | 62 | birthPlace; citizenship; spouse; officeHolder; deathPlace |
| case6_weighted | 154 | 5 | 194 | serviceBranch; awardedTo; award; dateOfRetirement; placeOfDeath |
| case6_weighted | 643 | 5 | 405 | offersSport; designatedAs; affiliatedWith; locatedAt; academicStaffSize |
| case1_name_only | 3 | 4 | 13 | architect; address; currentTenants; country |


## Per-Case Growth Plots

### case1_name_only

![case1_name_only growth](growth_case1_name_only.svg)

### case2_name_general

![case2_name_general growth](growth_case2_name_general.svg)

### case3_name_detail

![case3_name_detail growth](growth_case3_name_detail.svg)

### case4_detail_strict

![case4_detail_strict growth](growth_case4_detail_strict.svg)

### case5_concat

![case5_concat growth](growth_case5_concat.svg)

### case6_weighted

![case6_weighted growth](growth_case6_weighted.svg)

## Final Schema Relation Details

| case | relation | first_seen_idx | observed_in_case_json | head_type | tail_type | definition |
| --- | --- | --- | --- | --- | --- | --- |
| case1_name_only | CEO | 465 | True | Company | CEO | indicates that a company is led by a chief executive officer |
| case1_name_only | aboveSeaLevel | 925 | True | City | AboveSeaLevel | indicates that a city is located above a certain sea level |
| case1_name_only | absoluteMagnitude | 33 | True | Asteroid | AbsoluteMagnitude | indicates that an asteroid has a specific absolute magnitude |
| case1_name_only | absolute_magnitude | 447 | True | CelestialBody | AbsoluteMagnitude | represents the relationship where an asteroid has a specific brightness measurement |
| case1_name_only | actedIn | 111 | True | Actor | TelevisionSeries | indicates that an actor starred in a television series |
| case1_name_only | actor | 1086 | True | TelevisionShow | Actor | indicates that a show features actors in its cast |
| case1_name_only | address | 3 | True | ArchitecturalStructure | GeographicLocation | indicates that an architectural structure has a specific physical address |
| case1_name_only | adjacentCounty | 185 | True | County | County | represents the relationship where one county is geographically adjacent to another county |
| case1_name_only | affiliatedWith | 146 | True | EducationalInstitution | University | represents the relationship where an educational institution is associated with a university |
| case1_name_only | affiliation | 17 | True | Institute | University | indicates that an educational institution is associated with a university for academic purposes |
| case1_name_only | airedBananaman | 868 | True | BroadcastNetwork | TVSeries | represents the relationship where a broadcast network broadcasts a TV series |
| case1_name_only | airedOn | 124 | True | TVSeries | BroadcastingCompany | indicates that a TV series is broadcasted by a specific broadcasting company |
| case1_name_only | airedShowOn | 345 | True | BroadcastingCompany | EventDate | indicates that a broadcasting company aired a show on a specific date |
| case1_name_only | altitudeAboveSeaLevel | 15 | True | Airport | Altitude | indicates that an airport is at a specific altitude above sea level |
| case1_name_only | annualRevenue | 1157 | True | Company | AnnualRevenue | represents the total revenue generated by a company in a fiscal year |
| case1_name_only | anthem | 225 | True | Monarchy | NationalAnthem | represents the relationship where a monarchy has a national anthem |
| case1_name_only | apoapsis | 33 | True | Asteroid | Apoapsis | indicates that an asteroid has a specific apoapsis distance |
| case1_name_only | apolloCrewMember | 337 | True | HistoricalFigure | SpaceMission | indicates that a historical figure was a crew member of a space mission |
| case1_name_only | architect | 3 | True | ArchitecturalStructure | Architect | indicates that an architectural structure is designed by a professional architect |
| case1_name_only | are | 826 | True | Thing | Thing | indicates that a group of entities share a common identity or classification |
| case1_name_only | area | 200 | True | Country | Area | represents the relationship where a countrys geographical extent is quantified |
| case1_name_only | areaCode | 74 | True | Place | AreaCode | represents the relationship where a place is uniquely identified by a numeric area code |
| case1_name_only | assembledBy | 982 | True | Automobile | AutomotiveCompany | indicates that an automobile is manufactured by an automotive company |
| case1_name_only | assembledIn | 680 | True | Automobile | City | represents the relationship where a vehicle is produced within a city |
| case1_name_only | assemblyLineLocation | 39 | True | Vehicle | City | indicates that a vehicle was produced on an assembly line located within a city |
| case1_name_only | assemblyLocation | 409 | True | Automobile | City | represents the relationship where a vehicle is produced in a city |
| case1_name_only | associatedBand | 108 | True | Musician | Band | indicates that a musician is associated with a musical group |
| case1_name_only | associatedWith | 400 | True | Musician | Musician | indicates that a musician collaborates with another artist in musical projects |
| case1_name_only | attendedSchool | 93 | True | Individual | School | indicates that an individual studied at a specific educational institution |
| case1_name_only | author | 72 | True | Book | Author | indicates that a book is authored by an individual |
| case1_name_only | award | 154 | True | HistoricalFigure | MilitaryAward | indicates that a historical figure received a specific military award |
| case1_name_only | awardedBy | 349 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure received a military award from a branch of the armed forces |
| case1_name_only | awardedTechnicalCampusStatusTo | 131 | True | GovernmentAgency | EducationalInstitution | represents the relationship where a government agency grants a technical campus status to an educational institution |
| case1_name_only | awardingBody | 1044 | True | Individual | MilitaryBranch | indicates that an individual is awarded by a specific military branch |
| case1_name_only | band | 239 | True | Musician | Band | indicates that a musician is part of a band |
| case1_name_only | becameProfessional | 582 | True | Individual | Profession | indicates that an individual transitioned into a professional role |
| case1_name_only | beganMusicalCareer | 400 | True | Musician | Year | represents the relationship where a musician starts their professional music career |
| case1_name_only | birthDate | 13 | True | MilitaryPerson | Date | indicates that a military person was born on a specific date |
| case1_name_only | birthPlace | 13 | True | MilitaryPerson | City | indicates that a military person is born in a specific city |
| case1_name_only | birthYear | 34 | True | HistoricalFigure | Year | indicates that a historical figure was born in a specific year |
| case1_name_only | bodyStyle | 399 | True | Automobile | BodyStyle | represents the relationship where an automobile has a specific body style |
| case1_name_only | borderingCounty | 906 | True | County | County | indicates that a county shares borders with other counties |
| case1_name_only | bornIn | 4 | True | Individual | City | indicates that an individual is born in a specific city |
| case1_name_only | bornOn | 30 | True | Athlete | BirthDate | indicates that an athlete was born on a specific date |
| case1_name_only | bornWithin | 357 | True | Individual | Monarchy | indicates that an individual was born within a monarchy |
| case1_name_only | born_on | 805 | True | Astronaut | BirthDate | indicates that an astronaut was born on a specific date |
| case1_name_only | broadcastedBy | 6 | True | TVShow | BroadcastingCompany | indicates that a TV show is broadcast by a specific broadcasting company |
| case1_name_only | broughtUpBy | 250 | True | MediaCompany | AnimatedCharacter | represents the relationship where a media company is associated with a specific animated character |
| case1_name_only | buildStartDate | 965 | True | EducationalBuilding | TemporalValue | indicates that a building was constructed on a specific date |
| case1_name_only | builder | 105 | True | Locomotive | Company | represents the relationship where a locomotive is produced by a manufacturing company |
| case1_name_only | built | 966 | True | HistoricalStructure | Year | indicates that a historical structure was constructed in a specific year |
| case1_name_only | builtBy | 757 | True | EducationalBuilding | Architect | represents the relationship where an educational building is designed by an architect |
| case1_name_only | builtIn | 7 | True | HistoricalStructure | TimePeriod | indicates that a historical structure is constructed in a specific year |
| case1_name_only | builtOn | 278 | True | EducationalBuilding | ConstructionDate | indicates that an educational building was constructed on a specific date |
| case1_name_only | campusLocation | 410 | True | University | Road | indicates that a university is situated on a specific road within its campus |
| case1_name_only | campus_location | 563 | True | EducationalInstitution | Address | indicates that an educational institution has a specific campus location |
| case1_name_only | canBeVaryWith | 67 | True | Dessert | DairyProduct | indicates that a dessert can be prepared with a dairy product |
| case1_name_only | category | 104 | True |  |  |  |
| case1_name_only | ceremonialCounty | 830 | True | Town | CeremonialCounty | represents the relationship where a town is part of a ceremonial county |
| case1_name_only | championOf | 659 | True | SportsTeam | League | represents the relationship where a sports team is the champion of a league |
| case1_name_only | champions | 16 | True | SportsTeam | League | indicates that a sports team is the champion of a league |
| case1_name_only | championship | 920 | True | SportsClub | League | indicates that a sports club has won a specific league championship |
| case1_name_only | character | 688 | True | Actor | TelevisionSeries | indicates that an actor portrays a character in a television series |
| case1_name_only | citizens | 369 | True | Nation | Population | represents the relationship where a nation comprises a specific demographic group |
| case1_name_only | citizenship | 332 | True | Citizen | Thing | indicates that a citizen holds citizenship in a country |
| case1_name_only | city | 418 | True | EducationalInstitution | City | indicates that an educational institution is located in a specific city |
| case1_name_only | cityManager | 913 | True | City | Position | indicates that a city is led by a specific leadership role |
| case1_name_only | coach | 295 | True | Team | Coach | represents the relationship where a coach leads a sports team |
| case1_name_only | completedOn | 190 | True | ArchitecturalStructure | CompletionDate | indicates that an architectural structure is finished on a specific completion date |
| case1_name_only | completionDate | 112 | True | Structure | Year | indicates that a building was completed on a specific year |
| case1_name_only | constructedBy | 47 | True | Structure | Architect | represents the relationship where a structure is designed by an architect |
| case1_name_only | constructionEnd | 588 | True | EducationalBuilding | Date | indicates that an educational building was completed on a specific date |
| case1_name_only | constructionPeriod | 47 | True | Structure | Period | indicates that a structure was built within a specific time frame |
| case1_name_only | constructionStart | 361 | True | Facility | Temporal | indicates that a facilitys construction began on a specific date |
| case1_name_only | constructionStartDate | 1121 | True | EducationalBuilding | ConstructionStartDate | indicates that an educational building has a specific start date for construction |
| case1_name_only | contains | 542 | True | Dessert | DriedFruit | indicates that a dessert includes dried fruit as an ingredient |
| case1_name_only | containsAdministrativeTerritory |  | False | AdministrativeTerritory | AdministrativeTerritory | Indicates that an administrative territory contains another administrative territory. |
| case1_name_only | containsIngredient | 986 | True | Dish | Nutrition | indicates that a dish includes granola, shredded coconut, and raisins as nutritional ingredients |
| case1_name_only | containsSettlement | 104 | True | AdministrativeTerritory | Settlement | Indicates that an administrative territory contains a settlement such as a city or town. |
| case1_name_only | containsTeam | 284 | True | League | SportsTeam | represents the relationship where a league includes multiple sports teams |
| case1_name_only | corporateForm | 29 | True | Company | LegalForm | represents the relationship where a company has a specific legal form |
| case1_name_only | cosparId | 416 | True | SpaceMission | CosparId | represents the relationship where a space mission is uniquely identified by a COSPAR ID |
| case1_name_only | country | 3 | True | EducationalInstitution | Country | indicates that an educational institution is located in a specific country |
| case1_name_only | countryOfBirth | 356 | True | HistoricalFigure | Country | represents the relationship where a historical figure is born in a specific country |
| case1_name_only | countryOfCitizenship | 311 | True | Politician | Nation | indicates that a politician holds citizenship in a sovereign state |
| case1_name_only | countryOfOrigin | 316 | True | Musician | Country | indicates that a musician originates from a specific country |
| case1_name_only | countryOrigin | 369 | True | Sweet | Nation | indicates that a sweet dessert originates from a specific nation |
| case1_name_only | county | 7 | True | HistoricalStructure | County | indicates that a historical structure is situated within a county |
| case1_name_only | created | 459 | True | Author | Book | represents the relationship where an author produces a literary work |
| case1_name_only | creator | 6 | True | TVShow | Creator | represents the relationship where a TV show is created by a specific creator |
| case1_name_only | crew | 703 | True | HistoricalFigure | SpaceMission | indicates that a historical figure was a member of a specific space mission |
| case1_name_only | currency | 24 | True | GeopoliticalEntity | MonetaryUnit | indicates that a country uses a specific currency for transactions |
| case1_name_only | currentClub | 164 | True | Athlete | SportsTeam | represents the relationship where an athlete is currently associated with a sports team |
| case1_name_only | currentDirector | 835 | True | EducationalInstitution | Educator | indicates that an educational institution has a current director who is an educator |
| case1_name_only | currentLeader | 699 | True | Nation | Politician | represents the relationship where a nation is led by a political leader |
| case1_name_only | currentLocation | 187 | True | Company | Country | indicates that a company is headquartered in a specific country |
| case1_name_only | currentPosition | 156 | True | Politician | PoliticalOffice | represents the relationship where a politician holds a current political office position |
| case1_name_only | currentSenator | 476 | True | State | Politician | represents the relationship where a state is governed by a current senator |
| case1_name_only | currentTeam | 42 | True | Player | Team | represents the relationship where a player is currently associated with a specific team |
| case1_name_only | currentTenants | 3 | True | ArchitecturalStructure | EducationalInstitution | indicates that an architectural structure is currently occupied by an educational institution |
| case1_name_only | currentlyPlaysFor | 95 | True | Athlete | SportsTeam | indicates that an athlete is currently affiliated with a sports team |
| case1_name_only | dateOfBirth | 25 | True | Individual | BirthDate | indicates that an individual has a specific birth date |
| case1_name_only | dateOfDeath | 633 | True | HistoricalFigure | Thing | indicates that a historical figure has an unknown death date |
| case1_name_only | dateOfRetirement | 154 | True | HistoricalFigure | RetirementDate | indicates that a historical figure retired on a specific date |
| case1_name_only | dateOfRole | 633 | True | HistoricalFigure | HistoricalYear | indicates that a historical figure held a role in a specific year |
| case1_name_only | deathDate | 93 | True | Individual | DeathDate | indicates that an individual has a specific death date |
| case1_name_only | deathPlace | 28 | True | Politician | Nation | indicates that a politician died in a specific nation |
| case1_name_only | debutTeam | 425 | True | Player | Team | indicates that a player made their initial appearance for a specific team |
| case1_name_only | degree | 242 | True | HistoricalFigure | Degree | indicates that a historical figure earned a formal academic qualification |
| case1_name_only | designatedAs | 643 | True | EducationalInstitution | CampusDesignation | represents the relationship where an educational institution is given a specific designation or classification |
| case1_name_only | designatedTechnicalCampusStatusTo | 143 | True | Council | Institute | indicates that a council formally recognizes a technical education institution as a campus |
| case1_name_only | designed | 887 | True | Professional | Structure | indicates that a professional architect created the design for a constructed facility |
| case1_name_only | diedDateTime | 991 | True | Individual | DateTime | indicates that an individual died on a specific date and time |
| case1_name_only | diedIn | 4 | True | Individual | Country | indicates that an individual dies in a specific country |
| case1_name_only | diedOn | 582 | True | Individual | DeathDate | indicates that an individual passed away on a specific date |
| case1_name_only | directedBy | 254 | True | EducationalInstitution | Educator | indicates that an educational institution is led by an educator |
| case1_name_only | direction | 365 | True | AdministrativeDivision | GeographicalDirection | indicates that a territorial division is geographically positioned relative to another |
| case1_name_only | director | 131 | True | EducationalInstitution | Educator | represents the relationship where an educational institution is led by an educator |
| case1_name_only | discovered | 182 | True | Astronomer | AstronomicalBody | indicates that an astronomer identifies a celestial body |
| case1_name_only | discoveredAsteroid | 255 | True | Astronomer | AstronomicalBody | indicates that an astronomer identifies a new celestial body |
| case1_name_only | discoveredBy | 33 | True | Asteroid | Astronomer | indicates that an asteroid is identified by an astronomer |
| case1_name_only | discoveryDate | 33 | True | Asteroid | Date | indicates that an asteroids discovery is recorded with a specific date |
| case1_name_only | doctoralStudents | 240 | True | University | DoctoralStudentsCount | indicates that a university has a specific number of doctoral students enrolled |
| case1_name_only | draftPick | 518 | True | Athlete | DraftPick | indicates that an athlete is selected as a draft pick |
| case1_name_only | draftPickNumber | 1057 | True | Athlete | DraftPickNumber | indicates that an athlete is assigned a draft pick number |
| case1_name_only | earnings | 85 | True | Company | Earnings | indicates that a company generates financial income over a year |
| case1_name_only | eat | 790 | True | Dessert | Type | indicates that a dessert is consumed as a type of food |
| case1_name_only | educatedAt | 707 | True | FootballClub | Athlete | indicates that a football club has an athlete as a former member |
| case1_name_only | educates | 257 | True | University | StudentPopulation | indicates that a university enrolls a total number of students |
| case1_name_only | education | 53 | True | HistoricalFigure | Degree | indicates that a historical figure has earned a formal academic degree |
| case1_name_only | elevationAboveSeaLevel | 73 | True | City | ElevationAboveSeaLevel | indicates that a city has a specific elevation above sea level |
| case1_name_only | engineType | 65 | True |  |  |  |
| case1_name_only | enrollment | 70 | True | University | StudentCount | represents the relationship where a university has a specific number of students enrolled |
| case1_name_only | epoch | 64 | True | Asteroid | Time | represents the relationship where an asteroid reaches a specific epoch in its orbit |
| case1_name_only | epochDate | 958 | True | CelestialBody | Date | indicates that a celestial body has a specific reference date |
| case1_name_only | erectedIn | 638 | True | Monument | State | indicates that a monument is erected in a specific state |
| case1_name_only | established | 48 | True | HistoricalMonument | TimePeriod | indicates that a historical monument is founded in a specific year |
| case1_name_only | establishedIn | 165 | True | Monument | Year | indicates that a monument is created in a specific year |
| case1_name_only | establishmentYear | 138 | True | Monument | Year | indicates that a monument was established in a specific year |
| case1_name_only | ethnicGroup | 4 | True | Country | Group | represents the relationship where a country has a specific ethnic group |
| case1_name_only | ethnonym | 735 | True | Nation | EthnicGroup | represents the relationship where a nation has an ethnonym |
| case1_name_only | extinctionDate | 558 | True | AutomobileBrand | Year | represents the relationship where an automobile brand ceased operations on a specific year |
| case1_name_only | firstAired | 6 | True | TVShow | EventDate | indicates that a TV show marks its premiere on a specific date |
| case1_name_only | firstAiredBy | 698 | True | TelevisionShow | BroadcastingCompany | indicates that a television show is broadcasted by a specific broadcasting company |
| case1_name_only | firstAiredOn | 21 | True | Program | EventDate | indicates that a program was first broadcasted on a specific date |
| case1_name_only | firstAppearance | 260 | True | Film | AnimatedCharacter | represents the relationship where a film features its initial appearance of an animated character |
| case1_name_only | firstAppearedAsFilmCharacterIn | 779 | True | FilmCharacter | Film | represents the relationship where a characters first appearance in a film is specified |
| case1_name_only | firstAppearedIn | 824 | True | AnimatedCharacter | Film | represents the relationship where an animated characters debut is in a movie |
| case1_name_only | firstProducedIn | 199 | True | Automobile | Year | indicates that an automobile was first manufactured in a specific year |
| case1_name_only | firstProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was first manufactured in a specific year |
| case1_name_only | followedBy | 241 | True | Book | Book | indicates that one book series continues another in a narrative sequence |
| case1_name_only | follows | 585 | True | Book | Book | indicates that one book comes after another in a series |
| case1_name_only | foodServedAsDessert | 811 | True | Nation | Dessert | indicates that a nation serves a specific dessert as a dessert |
| case1_name_only | formerClub | 616 | True | Player | FootballClub | represents the relationship where a player was previously affiliated with a football club |
| case1_name_only | formerTeam | 186 | True | Player | Team | represents the relationship where a player was formerly part of a team |
| case1_name_only | formerlyPlayedFor | 782 | True | Athlete | SportsTeam | indicates that an athlete previously played for a sports team |
| case1_name_only | foundIn | 19 | True | DessertFood | Country | represents the relationship where a dessert food item is located within a specific country |
| case1_name_only | founded | 114 | True | Company | Date | indicates that a company was established on a specific date |
| case1_name_only | foundedBy | 120 | True | Company | Founder | represents the relationship where a company is initiated by a person |
| case1_name_only | founder | 62 | True | Company | Founder | represents the relationship where a company is initiated and managed by a founder |
| case1_name_only | founding | 691 | True | City | HistoricalFigure | represents the relationship where a city is founded by a historical figure |
| case1_name_only | foundingDate | 22 | True | PharmaceuticalCompany | FoundingDate | indicates that a pharmaceutical company was established on a specific founding date |
| case1_name_only | foundingEntity | 221 | True | BroadcastingCompany | FoundingEntity | represents the relationship where a broadcasting company is established by a founding entity |
| case1_name_only | foundingFather | 1014 | True | BroadcastingCompany | FoundingFather | represents the relationship where a broadcasting company was established by a founding father |
| case1_name_only | foundingPerson | 831 | True | Company | Founder | indicates that a company was founded by a specific person |
| case1_name_only | foundingPlace | 114 | True | Company | City | indicates that a company was founded in a specific city |
| case1_name_only | foundingYear | 1024 | True | Aerodrome | Year | indicates that an aerodrome was founded in a specific year |
| case1_name_only | from | 936 | True | Musician | Thing | indicates that a musician is associated with a specific geographic entity |
| case1_name_only | fullAddress | 392 | True | Institute | Address | indicates that an institute has a specific full physical address |
| case1_name_only | fullName | 203 | True | State | Name | indicates that a state has a formal name |
| case1_name_only | full_name | 246 | True | SportsTeam | SportsTeam | indicates that a sports team has a formal name |
| case1_name_only | gaveStatusBy | 857 | True | EducationalInstitution | EducationalAuthority | indicates that an educational institution is granted a status by an educational authority |
| case1_name_only | gaveTechnicalCampusStatusTo | 392 | True | Council | Institute | indicates that a council grants a specific status to a technical education institution |
| case1_name_only | genre | 91 | True | TV_series | Series | indicates that a TV series belongs to a specific series category |
| case1_name_only | giverOfStatus | 1070 | True | EducationalInstitution | GovernmentAgency | indicates that a government agency grants a designation or accreditation to an educational institution |
| case1_name_only | governingBody | 748 | True | City | Position | indicates that a city is governed by a specific leadership position |
| case1_name_only | governmentForm | 1036 | True | StateFormOfGovernment | UnitaryState | indicates that a state form of government is characterized by a centralized system of governance |
| case1_name_only | governmentType | 1 | True |  |  |  |
| case1_name_only | governor | 925 | True | City | GovernmentBody | indicates that a city is governed by a government body |
| case1_name_only | graduatedFrom | 557 | True | Historian | Institution | indicates that a historian received their education from an academic institution |
| case1_name_only | graduatedIn | 477 | True | HistoricalFigure | Year | indicates that a historical figure graduated in a specific year |
| case1_name_only | graduationYear | 242 | True | HistoricalFigure | GraduationYear | indicates that a historical figure completed an educational program in a specific year |
| case1_name_only | ground | 16 | True | Stadium | SportsTeam | indicates that a stadium hosts a sports team |
| case1_name_only | grounds | 675 | True | SportsTeam | Stadium | indicates that a sports team has a specific ground or stadium |
| case1_name_only | hadCampusIn | 492 | True | University | City | indicates that a university had its campus within a specific city |
| case1_name_only | has | 48 | True | AdministrativeDivision | AdministrativeDivision | indicates that a territorial division contains another territorial division |
| case1_name_only | hasBird | 282 | True | State | Species | represents the relationship where a state is associated with a specific bird species |
| case1_name_only | hasCylinderCount | 426 | True | Locomotive | CylinderCount | indicates that a locomotive has a specific number of cylinders |
| case1_name_only | hasDessert | 791 | True | City | SweetDish | indicates that a city has a specific dessert dish |
| case1_name_only | hasDoctoralStudents | 462 | True | University | DoctoralStudents | indicates that a university enrolls a specific number of doctoral students |
| case1_name_only | hasEngine | 426 | True | Locomotive | Engine | indicates that a locomotive is equipped with a specific type of engine |
| case1_name_only | hasFood | 945 | True | Nation | Dessert | indicates that a nation includes a specific type of food in its culinary offerings |
| case1_name_only | hasIngredient | 892 | True | Dessert | Ingredient | indicates that a dessert contains a specific ingredient |
| case1_name_only | hasItem | 171 | True | UrbanCenter | SweetFood | represents the relationship where an urban center has another specific type of sweet food item |
| case1_name_only | hasMember | 360 | True | Band | Musician | represents the relationship where a band comprises a musician |
| case1_name_only | hasNativeBird | 505 | True | State | Bird | represents the relationship where a state is home to a specific native bird species |
| case1_name_only | hasOfficial | 493 | True | State | Official | represents the relationship where a state appoints an official to lead its administration |
| case1_name_only | hasPart | 727 | True | GeographicArea | GeographicArea | represents the relationship where one geographic area contains another |
| case1_name_only | hasPopulationDensity | 669 | True | Country | PopulationDensity | represents the relationship where a country has a specific population density |
| case1_name_only | hasProperty | 836 | True | City | Monument | indicates that a city has a specific historical or commemorative monument |
| case1_name_only | hasSenator | 789 | True | State | Politician | represents the relationship where a state has a senator |
| case1_name_only | hasSubsidiary | 85 | True | Company | Subsidiary | represents the relationship where a company maintains a subsidiary organization |
| case1_name_only | hasTeam | 524 | True | ProfessionalLeague | SportsClub | represents the relationship where a professional league has a team belonging to a sports club |
| case1_name_only | hasVariation | 985 | True | Dessert | Dessert | indicates that a dessert has a variation of another dessert |
| case1_name_only | headquarteredIn | 386 | True | University | City | indicates that a university is geographically located within a specific city |
| case1_name_only | headquarters | 111 | True | TelevisionNetwork | Headquarters | indicates that a television network has its administrative center in a specific building |
| case1_name_only | headquartersLocation | 99 | True | AirlineCompany | City | indicates that an airline company has its headquarters in a city |
| case1_name_only | height | 90 | True | Athlete | Height | indicates that an athlete has a specific height measurement |
| case1_name_only | heldOfficeWhile | 862 | True | Politician | Politician | indicates that a politician held office during the tenure of another politician |
| case1_name_only | homeGround | 88 | True | SportsTeam | Stadium | indicates that a sports team has a designated home ground venue |
| case1_name_only | icaoIdentifier | 355 | True | Aerodrome | ICAOIdentifier | indicates that an aerodrome is assigned a unique ICAO identifier |
| case1_name_only | icaoLocationIdentifier | 14 | True | Aerodrome | ICAOIdentifier | represents the relationship where an aerodrome is assigned a unique ICAO identifier |
| case1_name_only | inBand | 301 | True | Musician | Band | represents the relationship where a musician is part of a musical group |
| case1_name_only | inOfficeWith | 344 | True | Politician | Politician | indicates that two politicians held office simultaneously |
| case1_name_only | industry | 187 | True | Company | BuildingMaterials | represents the relationship where a company operates within a specific industry category |
| case1_name_only | ingredient | 147 | True | MexicanDessert | DairyProduct | indicates that a Mexican dessert contains a dairy-based ingredient |
| case1_name_only | ingredients | 24 | True | DessertFood | FoodIngredients | indicates that a dessert food is composed of specific ingredients |
| case1_name_only | inhabitant | 24 | True | GeopoliticalEntity | HumanPopulation | represents the relationship where a country is populated by its inhabitants |
| case1_name_only | inhabitants | 67 | True | Country | Population | indicates that a country is inhabited by a population |
| case1_name_only | inhabitedBy | 485 | True | Mexico | HumanPopulation | represents the relationship where the inhabitants of Mexico are the Mexicans |
| case1_name_only | inhabits | 853 | True | State | Bird | represents the relationship where a state is home to a specific bird species |
| case1_name_only | is | 826 | True | Thing | Thing | represents the relationship where an entity belongs to a specific category |
| case1_name_only | isA | 19 | True |  |  |  |
| case1_name_only | isAffiliatedTo | 133 | True |  |  |  |
| case1_name_only | isAffiliatedWith | 198 | True |  |  |  |
| case1_name_only | isAnEthnicGroup | 1034 | True |  |  |  |
| case1_name_only | isAssociatedWith | 131 | True |  |  |  |
| case1_name_only | isBasedAt | 345 | True | BroadcastingCompany | Building | indicates that a broadcasting company operates from a physical workplace |
| case1_name_only | isBasedIn | 51 | True | Airport | City | indicates that an airport is geographically located within a city |
| case1_name_only | isCapitalOf | 669 | True | Country | Country | represents the relationship where a country is the capital of itself |
| case1_name_only | isCategorizedAs | 48 | True | HistoricalMonument | HistoricProperty | indicates that a historical monument is classified as a significant property |
| case1_name_only | isCategory | 836 | True |  |  |  |
| case1_name_only | isChampion | 82 | True | SportsClub | BooleanValue | indicates that a sports club is the champion of a league |
| case1_name_only | isChiefOf | 866 | True | HistoricalFigure | AerospaceAgency | indicates that a historical figure leads an aerospace agency |
| case1_name_only | isContributing_Property | 873 | True | HistoricalMonument | TrueValue | represents the relationship where a historical monument is considered significant or contributing to a site |
| case1_name_only | isDessert | 791 | True | SweetDish | LogicalValue | represents the relationship where a dessert dish is classified as a dessert |
| case1_name_only | isEthnicGroup | 437 | True | Community | Nation | indicates that an ethnic group belongs to a sovereign nation |
| case1_name_only | isEthnicGroupIn | 882 | True | Ethnicity | Nation | a relation between Ethnicity and Nation |
| case1_name_only | isFoundationPlace | 499 | True | FoundationPlace | FoundationPlace | indicates that a FoundationPlace serves as the origin or basis of another FoundationPlace |
| case1_name_only | isFrom | 725 | True | Individual | Thing | indicates that an individual is from a specific entity |
| case1_name_only | isHomeTo | 466 | True | EducationalBuilding | EducationalInstitution | indicates that an educational building houses an educational institution |
| case1_name_only | isInhabitedBy | 860 | True | Nation | Population | indicates that a nation is populated by a specific demographic group |
| case1_name_only | isLeaderIn | 1160 | True | Politician | Nation | indicates that a politician leads a nation |
| case1_name_only | isLeaderOf | 303 | True | Politician | Thing | indicates that a politician holds leadership over a specific entity |
| case1_name_only | isLocatedAt | 650 | True | EducationalInstitution | City | indicates that an educational institution is physically situated within a city |
| case1_name_only | isLocatedIn | 48 | True | HistoricalMonument | Municipality | indicates that a historical monument is located within a populated place |
| case1_name_only | isLocationOf | 969 | True | Country | Population | represents the relationship where a country is the location of its population |
| case1_name_only | isManagedBy | 367 | True | City | GovernmentPosition | indicates that a city is managed by a specific government position |
| case1_name_only | isMemberOf | 50 | True | Musician | Band | represents the relationship where a musician is part of a musical group |
| case1_name_only | isNationalityOf | 669 | True | Country | Individual | indicates that a country is the nationality of an individual |
| case1_name_only | isNear | 744 | True | HistoricalMonument | County | indicates that a historical monument is located near another county |
| case1_name_only | isPartOf | 1 | True | City | State | indicates that a city is administratively part of a state |
| case1_name_only | isServedAs | 305 | True | FoodItem | MealComponent | represents the relationship where a food item is part of a meal course |
| case1_name_only | isServedBy | 354 | True | Autodrome | Aerodrome | indicates that an autodrome is served by another location |
| case1_name_only | isStarOf | 345 | True | Actor | TVShow | indicates that an actor performs in a television show |
| case1_name_only | isType | 1077 | True |  |  |  |
| case1_name_only | isWestOf | 836 | True | City | County | indicates that a city is located west of a county |
| case1_name_only | jobTitle | 771 | True | MilitaryPerson | MilitaryRole | indicates that a military person holds a specific combat leadership role |
| case1_name_only | keyPerson | 461 | True | PharmaceuticalCompany | Executive | represents the relationship where a pharmaceutical company is led by a high-ranking executive |
| case1_name_only | keyPersonAt | 1048 | True | KeyPerson | Company | indicates that a key person holds a significant role within a company organization |
| case1_name_only | keyPersonFor | 609 | True | KeyPerson | Company | indicates that a key person oversees a company |
| case1_name_only | keyPersonIn | 818 | True | KeyPerson | Company | indicates that a key person holds a significant role within a company organization |
| case1_name_only | language | 340 | True | Nation | ModernLanguage | represents the relationship where a nation employs a modern form of a language |
| case1_name_only | lastAired | 472 | True | Broadcast | EventDate | indicates that a broadcast program concludes on a specific event date |
| case1_name_only | lastAiredOn | 167 | True | Program | Date | indicates that a program was last aired on a specific date |
| case1_name_only | lastProducedIn | 199 | True | Automobile | Year | indicates that an automobile was last manufactured in a specific year |
| case1_name_only | lastProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was last manufactured in a specific year |
| case1_name_only | laterCrewMemberOf | 602 | True | HistoricalFigure | SpaceMission | indicates that a historical figure serves as a crew member on a space mission |
| case1_name_only | leader | 196 | True | City | Politician | represents the relationship where a city is governed by a political leader |
| case1_name_only | leaderName | 251 | True | City | Leader | represents the relationship where a city is led by a specific person |
| case1_name_only | leaderTitle | 1 | True | City | LeaderTitle | indicates that a city has a leadership role title |
| case1_name_only | leadershipTitle | 280 | True | Country | LeadershipRole | indicates that a country has a specific title for its leadership role |
| case1_name_only | league | 16 | True | SportsTeam | League | indicates that a sports team competes in a specific league |
| case1_name_only | leagueTitle | 975 | True | SportsTeam | League | indicates that a sports team competes in a specific league title |
| case1_name_only | length | 2 | True | Locomotive | Length | represents the relationship where a locomotives physical dimension is defined |
| case1_name_only | locatedAboveSeaLevel | 83 | True | Airport | Altitude | indicates that an airport is at a specific elevation above sea level |
| case1_name_only | locatedAt | 643 | True | EducationalInstitution | Address | represents the specific address or location of an educational institution |
| case1_name_only | locatedIn | 346 | True | HistoricalMonument | County | indicates that a historical monument is geographically located within a county |
| case1_name_only | locatedInAdministrativeTerritory |  | False | Location | AdministrativeTerritory | Indicates that a location is located within a specific administrative territorial entity. |
| case1_name_only | locatedInCountry |  | False | Location | Country | Indicates that a location is located in a country. |
| case1_name_only | location | 0 | True | Company | City | represents the relationship where a companys physical presence is located within a city |
| case1_name_only | locationCity | 872 | True | BroadcastingCompany | City | indicates that a broadcasting company is headquartered in a specific city |
| case1_name_only | locationElevation | 56 | True | Aerodrome | Elevation | indicates that an aerodrome has a specific elevation above sea level |
| case1_name_only | locationInTimezone | 852 | True | City | Zone | indicates that a city is located in a specific time zone |
| case1_name_only | locationOf | 707 | True | Stadium | FootballClub | indicates that a stadium is associated with a specific football club |
| case1_name_only | locationOfBroadcast | 167 | True | Program | Building | indicates that a program is broadcast from a specific building |
| case1_name_only | locationOfDeath | 173 | True | Country | Country | indicates that a country is the location of an individual's death |
| case1_name_only | locationOfFounding | 808 | True | Company | City | indicates that a company was founded in a specific city location |
| case1_name_only | locationOfOccurrence | 449 | True | Ingredient | Country | indicates that an ingredient is found within a specific country |
| case1_name_only | locationRelation | 78 | True | County | SpatialRelation | represents the relationship where a county is situated relative to another county in a north-south direction |
| case1_name_only | longName | 174 | True | Nation | OfficialName | represents the relationship where a nations long name corresponds to its official name |
| case1_name_only | madeAutomobile | 507 | True | AutomobileCompany | Automobile | represents the relationship where an automobile company creates a vehicle product |
| case1_name_only | magnitude | 739 | True | Asteroid | Magnitude | indicates that an asteroid has a numerical measure of its brightness |
| case1_name_only | mainDishType | 421 | True |  |  |  |
| case1_name_only | mainIngredient | 329 | True | Dessert | DairyProduct | indicates that a dessert contains raisins |
| case1_name_only | mainProduct | 27 | True | Company | Software | represents the relationship where a company specializes in creating software products |
| case1_name_only | makes | 22 | True | PharmaceuticalCompany | Medicine | indicates that a pharmaceutical company produces medical products |
| case1_name_only | manager | 5 | True | SportsTeam | Manager | indicates that a sports team is led by a manager |
| case1_name_only | managerOfCurrentTeam | 572 | True | Athlete | Manager | indicates that an athlete has a manager for their current team |
| case1_name_only | managerTitle | 29 | True | Company | ManagerTitle | indicates that a company is managed by a specific title |
| case1_name_only | manages | 192 | True | Athlete | Coach | represents the relationship where an athlete oversees a coaching role |
| case1_name_only | manufacturer | 150 | True | Locomotive | Manufacturer | indicates that a locomotive is produced by a specific manufacturer |
| case1_name_only | manufacturingEndDate | 325 | True | AutomobileModel | ManufacturingEndDate | represents the relationship where a specific vehicle model has a defined end date for production |
| case1_name_only | marriage | 640 | True | Individual | Individual | indicates that two individuals are legally or socially united in marriage |
| case1_name_only | member | 343 | True | Band | Musician | indicates that a band has a musician as one of its members |
| case1_name_only | memberOf | 30 | True | Athlete | YouthTeam | indicates that an athlete is a member of a youth sports team |
| case1_name_only | mission | 25 | True | Individual | SpaceMission | indicates that an individual participates in a spaceflight mission |
| case1_name_only | monumentCategory | 955 | True |  |  |  |
| case1_name_only | monumentLocation | 955 | True | MilitaryUnit | County | represents the relationship where a military units monument is located within a county |
| case1_name_only | movedTo | 1161 | True | Company | Country | indicates that a company relocated to a specific country |
| case1_name_only | municipality | 7 | True | HistoricalStructure | City | indicates that a historical structure is located within a city |
| case1_name_only | name | 479 | True | Stadium | Stadium | indicates that a stadium has a specific name |
| case1_name_only | nationalAnthem | 269 | True | Government | NationalAnthem | represents the relationship where a government holds a national anthem |
| case1_name_only | nationality | 11 | True | Individual | Country | indicates that an individual belongs to a specific country |
| case1_name_only | nativeOf | 477 | True | State | Bird | indicates that a state is the native home of a bird species |
| case1_name_only | nativeState | 884 | True | Bird | State | represents the relationship where a bird species is native to a specific state |
| case1_name_only | neighbor | 138 | True | County | County | represents the relationship where a county is geographically adjacent to another county |
| case1_name_only | netIncome | 149 | True | Company | NetIncome | represents the relationship where a companys net income is a specific financial metric |
| case1_name_only | network | 91 | True | TV_series | BroadcastingCompany | indicates that a TV series is broadcasted by a broadcasting company |
| case1_name_only | nickname | 88 | True | SportsTeam | Nickname | represents the relationship where a sports team has a distinctive nickname |
| case1_name_only | northNeighbour | 165 | True | County | County | indicates that a county is geographically located north of another county |
| case1_name_only | northOf | 528 | True | County | County | indicates that one county is geographically situated north of another |
| case1_name_only | numberOfAcademicStaff | 522 | True | EducationalInstitution | NumberOfStaff | indicates that an educational institution has a total number of academic staff |
| case1_name_only | numberOfDoctoralStudents | 237 | True | University | Number_of_DoctoralStudents | indicates that a university has a specific count of doctoral students enrolled |
| case1_name_only | numberOfEmployees | 114 | True | Company | Number | indicates that a company has a specific number of employees |
| case1_name_only | numberOfMembers | 5 | True | SportsTeam | Number | indicates that a sports team has a specific number of members |
| case1_name_only | numberOfPages | 72 | True | Book | Pages | indicates that a book has a specific number of pages |
| case1_name_only | numberOfPostgraduateStudents | 406 | True | EducationalInstitution | PostgraduateStudents | indicates that an educational institution has a specific number of postgraduate students enrolled |
| case1_name_only | numberOfStaff | 900 | True | University | Number | indicates that a university employs a specific number of staff members |
| case1_name_only | numberOfStaffMembers | 448 | True | University | NumberOfStaffMembers | indicates that a university has a specific number of staff members |
| case1_name_only | numberOfStudents | 66 | True | University | StudentCount | indicates that a university has a total count of students including various levels and staff members |
| case1_name_only | numberOfUndergraduateStudents | 118 | True | University | Number | indicates that a university has a specific count of undergraduate students |
| case1_name_only | occupation | 13 | True | MilitaryPerson | MilitaryOccupation | indicates that a military person holds a specific military role |
| case1_name_only | offersProduct | 525 | True | MediaCompany | Software | represents the relationship where a media company provides software products |
| case1_name_only | offersServices | 737 | True | Company | WebServices | represents the relationship where a company provides services related to the World Wide Web |
| case1_name_only | offersSport | 556 | True | EducationalInstitution | Activity | indicates that an educational institution offers a specific sport |
| case1_name_only | officeHolder | 28 | True | Politician | Politician | indicates that a politician holds a position equivalent to another politician |
| case1_name_only | officialLanguage | 183 | True | State | OfficialLanguage | represents the relationship where a state has a primary official language |
| case1_name_only | officialName | 1162 | True | Nation | OfficialName | represents the relationship where a nations official name is its primary identifier |
| case1_name_only | operatedBy | 10 | True | Airbase | MilitaryBranch | indicates that an airbase is managed by a military branch |
| case1_name_only | operates | 51 | True | Airline | Airport | indicates that an airline manages an airport facility |
| case1_name_only | operatingArea | 802 | True | Company | Country | represents the relationship where a company operates within a specific country |
| case1_name_only | operatingEntity | 942 | True | Airbase | MilitaryBranch | represents the relationship where an airbase is managed by a military branch |
| case1_name_only | operatingOrganisation | 355 | True |  |  |  |
| case1_name_only | operatingOrganisationFor | 463 | True |  |  |  |
| case1_name_only | operatingOrganization | 132 | True | Aerodrome | OperatingOrganization | represents the relationship where an aerodrome is managed by an operating organization |
| case1_name_only | operator | 40 | True | Airport | AeronauticsCompany | indicates that an airport is managed by an aeronautics company |
| case1_name_only | orbitalPeriod | 33 | True | Asteroid | OrbitalPeriod | indicates that an asteroid has a specific orbital period |
| case1_name_only | orbital_period | 135 | True | Asteroid | OrbitalPeriod | indicates that an asteroid has a duration for its orbit around its primary body |
| case1_name_only | origin | 630 | True | Musician | City | indicates that a musician originates from a specific city |
| case1_name_only | originCountry | 1150 | True | Dessert | Nation | represents the relationship where a dessert is associated with a country of origin |
| case1_name_only | otherTeam | 395 | True | Athlete | SportsTeam | indicates that an athlete is associated with another sports team |
| case1_name_only | ownedBy | 374 | True | Structure | EducationalInstitution | indicates that a structure is owned by an educational institution |
| case1_name_only | owner | 38 | True | EducationalFacility | EducationalInstitution | indicates that an educational institution owns a specific facility |
| case1_name_only | owns | 9 | True | EducationalInstitution | EducationalFacility | indicates that an educational institution possesses a specific educational facility |
| case1_name_only | parent | 111 | True | Actor | Daughter | indicates that an actor has a daughter |
| case1_name_only | parentCompany | 609 | True | Company | Company | represents the relationship where a company is the parent entity of another company |
| case1_name_only | partOf | 977 | True | Astronaut | SpaceMission | represents the relationship where an astronaut is part of a spaceflight undertaking |
| case1_name_only | partOfMission | 897 | True | MilitaryPerson | SpaceMission | indicates that a military person is part of a specific space mission |
| case1_name_only | participatedIn | 220 | True | Fighter_pilot | SpaceMission | represents the relationship where a fighter pilot participates in a space mission |
| case1_name_only | peopleName | 171 | True | Nation | PeopleGroup | represents the relationship where a nation has a specific name for its people |
| case1_name_only | periapsis | 49 | True | Asteroid | Periapsis | indicates that an asteroid has a specific periapsis distance |
| case1_name_only | placeOfBirth | 154 | True | HistoricalFigure | State | indicates that a historical figure was born in a specific state |
| case1_name_only | placeOfDeath | 154 | True | HistoricalFigure | State | indicates that a historical figure died in a specific state |
| case1_name_only | placeOfOrigin | 52 | True | Individual | State | indicates that an individuals place of origin is within a specific state |
| case1_name_only | playIn | 293 | True | SportsTeam | League | indicates that a sports team competes in a league organized by a governing body |
| case1_name_only | playInLeague | 319 | True | SportsTeam | ProfessionalLeague | represents the relationship where a sports team is affiliated with a professional sports league |
| case1_name_only | playedBy | 430 | True | League | SportsTeam | indicates that a league is contested by multiple sports teams |
| case1_name_only | playedFor | 95 | True | Athlete | SportsTeam | indicates that an athlete competes for a sports team |
| case1_name_only | playedIn | 179 | True | SportsClub | Year | indicates that a sports club participated in a competition in a specific year |
| case1_name_only | playedInSeason | 495 | True | SportsTeam | Year | indicates that a sports team participated in a season |
| case1_name_only | playedWith | 20 | True | Musician | Band | indicates that a musician is a member of a band |
| case1_name_only | playground | 1101 | True | SportsClub | Stadium | indicates that a sports club has a designated sports facility |
| case1_name_only | playsFor | 700 | True | Athlete | SportsTeam | indicates that an athlete competes for a sports team |
| case1_name_only | playsIn | 566 | True | SportsTeam | ProfessionalLeague | indicates that a sports team competes in a professional league |
| case1_name_only | playsInstrument | 50 | True | Musician | MusicalInstrument | indicates that a musician uses a specific musical instrument in their performances |
| case1_name_only | playsMusic | 607 | True | Musician | Genre | indicates that a musician performs music within a specific genre |
| case1_name_only | population | 1 | True | City | Population | indicates that a city has a total population count |
| case1_name_only | populationDensity | 1 | True | City | PopulationDensity | indicates that a city has a specific population density |
| case1_name_only | populationMetro | 31 | True | City | Population | indicates that a city has a total population count within its metropolitan area |
| case1_name_only | populationTotal | 273 | True | DemographicEntity | Population | represents the relationship where a countrys total population is specified |
| case1_name_only | position | 217 | True | Politician | LegislativeOffice | indicates that a politician holds a legislative office position |
| case1_name_only | postalCode | 296 | True | Village | PostalCode | represents the relationship where a village is linked to a standardized alphanumeric postal code |
| case1_name_only | postalCodeRange | 561 | True | City | PostalCodeRange | represents the relationship where a citys postal codes are grouped within a specific range |
| case1_name_only | postgraduateStudentCount | 521 | True | University | PostgraduateStudentCount | represents the relationship where a university has a specific number of post-graduate students |
| case1_name_only | postgraduateStudents | 66 | True | University | PostgraduateStudents | indicates that a university has a specific number of students enrolled in postgraduate programs |
| case1_name_only | powerType | 2 | True |  |  |  |
| case1_name_only | precedes | 100 | True | FantasyWork | FantasyWork | indicates that one work of fiction follows another in a chronological order |
| case1_name_only | prequelOf | 396 | True | Book | Book | represents the relationship where one book is a prequel to another |
| case1_name_only | president | 691 | True | EducationalInstitution | Individual | indicates that an educational institution is led by an individual holding a leadership position |
| case1_name_only | presidentDuringService | 326 | True | Politician | Politician | indicates that a politician served during the presidency of another politician |
| case1_name_only | presidentDuringTenure | 311 | True | Politician | Politician | represents the relationship where a politician serves as president during a specific tenure |
| case1_name_only | previousChampion | 88 | True | SportsTeam | SportsTeam | indicates that a sports team has previously won a championship |
| case1_name_only | previousChampions | 419 | True | League | SportsClub | represents the relationship where a league has previously been won by a sports club |
| case1_name_only | previousPosition | 914 | True | HistoricalFigure | ProfessionalRole | indicates that a historical figure held a previous professional role |
| case1_name_only | previousRole | 90 | True | Athlete | TeamRole | indicates that an athlete held a specific role in a previous team |
| case1_name_only | previousTeam | 90 | True | Athlete | SportsTeam | indicates that an athlete previously played for a different sports team |
| case1_name_only | previouslyLedBy | 1097 | True | City | Politician | represents the relationship where a city was previously governed by a political leader |
| case1_name_only | produced | 208 | True | AutomotiveCompany | Automobile | indicates that an automotive company manufactures a specific vehicle model |
| case1_name_only | produces | 27 | True | Company | Software | indicates that a company manufactures or develops software products |
| case1_name_only | product | 187 | True | Company | HeatingVentilationAir Conditioning | indicates that a company produces a specific type of product |
| case1_name_only | productionEndYear | 60 | True | Automobile | Year | indicates that an automobile ends production in a specific year |
| case1_name_only | productionLocation | 137 | True | Automobile | State | indicates that an automobile is manufactured in a specific state |
| case1_name_only | productionPeriod | 281 | True | Locomotive | ProductionPeriod | indicates that a locomotive was manufactured within a specific time frame |
| case1_name_only | productionStartYear | 60 | True | Automobile | Year | indicates that an automobile begins production in a specific year |
| case1_name_only | propertyOf | 244 | True | ArchitecturalStructure | University | indicates that a university owns the architectural structure |
| case1_name_only | publicationDate | 253 | True | FantasyNovel | PublicationDate | represents the relationship where a fantasy novel has a specific release date |
| case1_name_only | published | 253 | True | Publisher | FantasyNovel | indicates that a publisher releases a fantasy novel into the market |
| case1_name_only | publisher | 100 | True | FantasyWork | Publisher | indicates that a publisher is responsible for the publication of a work of fiction |
| case1_name_only | receivedAward | 53 | True | HistoricalFigure | MilitaryAward | indicates that a historical figure has been awarded a military honor |
| case1_name_only | region | 26 | True | Dessert | GeographicArea | indicates that a dessert is associated with a specific geographic region |
| case1_name_only | relateto | 7 | True | County | County | indicates that two counties are geographically adjacent to each other |
| case1_name_only | relationTo | 459 | True | Book | Book | represents the relationship where one book is related to another book |
| case1_name_only | relationToOther | 688 | True | Actor | Daughter | represents the relationship where an actor is the father of another person |
| case1_name_only | relationTo_Alan_Shepard | 840 | True | EducationalInstitution | Graduation | represents the relationship where an educational institution is associated with an individual completing an educational program |
| case1_name_only | relativePositionTo | 555 | True | County | County | indicates that one county is geographically positioned relative to another county |
| case1_name_only | relativerelation | 678 | True | County | GeographicalRelation | represents the relationship where a county is positioned relative to another location |
| case1_name_only | releaseDate | 172 | True | Book | ReleaseDate | indicates that a book was released on a specific date |
| case1_name_only | represented | 217 | True | Politician | State | indicates that a politician represents a specific state |
| case1_name_only | requires | 860 | True | SweetDish | FoodItem | indicates that a dessert requires a specific food item as an ingredient |
| case1_name_only | retired | 599 | True | HistoricalFigure | Date | indicates that a historical figure retires on a specific date |
| case1_name_only | retiredOn | 69 | True | HistoricalFigure | Date | indicates that a historical figure retired on a specific date |
| case1_name_only | retirementDate | 615 | True | HistoricalFigure | RetirementDate | indicates that a historical figure retires on a specific date |
| case1_name_only | revenue | 117 | True | Company | Revenue | represents the relationship where a company generates a specific amount of income |
| case1_name_only | role | 332 | True | Citizen | Professional | indicates that a citizen holds a specific professional role |
| case1_name_only | rotationPeriod | 33 | True | Asteroid | RotationPeriod | indicates that an asteroid has a specific rotation period |
| case1_name_only | rotation_period | 103 | True | Planet | Duration | indicates that a planet completes one rotation in a given duration |
| case1_name_only | rotationalPeriod | 109 | True | Asteroid | RotationalPeriod | indicates that an asteroid rotates on its axis in a specific amount of time |
| case1_name_only | runwayLength | 10 | True | Airbase | RunwayLength | indicates that an airbase has a specific runway length |
| case1_name_only | runwayMaterial | 249 | True | Aerodrome | Concrete | represents the relationship where an aerodrome runway is constructed with concrete |
| case1_name_only | runwayName | 40 | True | Airport | RunwayName | indicates that an airport has a specific runway name for identification |
| case1_name_only | runwaySurface | 122 | True | Aerodrome | Concrete | indicates that an aerodrome has a runway surface made of concrete |
| case1_name_only | selectedBy | 11 | True | Individual | GovernmentAgency | indicates that an individual is selected by a governmental agency |
| case1_name_only | selectedYear | 337 | True | HistoricalFigure | SelectionYear | indicates that a historical figure was selected in a specific year |
| case1_name_only | selectionYear | 11 | True | GovernmentAgency | Year | indicates that a governmental agency selects individuals in a specific year |
| case1_name_only | sells | 22 | True | PharmaceuticalCompany | PersonalCareProduct | indicates that a pharmaceutical company offers personal care products |
| case1_name_only | servedAs | 19 | True | DessertFood | Dessert | indicates that a dessert food item is specifically prepared as a sweet course at the end of a meal |
| case1_name_only | servedAt | 485 | True | SweetDish | DessertCourse | indicates that a sweet dish is served as part of a dessert course |
| case1_name_only | servedBy | 1155 | True | Aerodrome | Autodrome | represents the relationship where an aerodrome is managed by an autodrome |
| case1_name_only | servedFor | 569 | True | SweetDish | SweetMeal | indicates that a sweet dish is typically served as a dessert course |
| case1_name_only | serves | 92 | True | Airport | Autodrome | indicates that an airport provides services to a nearby auto racing facility |
| case1_name_only | serviceBranch | 154 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure served in a specific military branch |
| case1_name_only | shownBy | 388 | True | Film | BroadcastingCompany | indicates that a film is broadcasted by a specific broadcasting company |
| case1_name_only | singsIn | 716 | True | Musician | Band | represents the relationship where a musician is a member of a musical group |
| case1_name_only | southeastNeighbor | 501 | True | AdministrativeDivision | AdministrativeDivision | indicates that an administrative division is geographically located to the southeast of another |
| case1_name_only | southeastNeighbour | 165 | True | County | County | indicates that a county is geographically located southeast of another county |
| case1_name_only | southeast_of | 104 | True | County | County | indicates that one county is located southeast of another county |
| case1_name_only | southwestNeighbour | 165 | True | County | County | indicates that a county is geographically located southwest of another county |
| case1_name_only | sportsOffered | 522 | True | EducationalInstitution | RecreationalSport | indicates that an educational institution offers a recreational sport |
| case1_name_only | spouse | 28 | True | Politician | Individual | indicates that a politician is married to an individual |
| case1_name_only | staffCount | 871 | True | University | StaffCount | indicates that a university has a total number of staff members employed |
| case1_name_only | staffMembers | 66 | True | University | StaffMembers | indicates that a university has a specific number of individuals employed by the institution |
| case1_name_only | staffSize | 352 | True | University | StaffSize | indicates that a university has a number of staff members |
| case1_name_only | starredBy | 867 | True | TelevisionShow | Actor | indicates that a television show features a specific actor |
| case1_name_only | starredIn | 472 | True | Actor | Broadcast | represents the relationship where an actor participates in a broadcast program |
| case1_name_only | starring | 91 | True | TV_series | Individual | indicates that a TV series features individual actors |
| case1_name_only | startDate | 544 | True | Structure | TemporalUnit | indicates that a building structure began construction at a specific date |
| case1_name_only | startDateConstruction | 112 | True | Structure | Year | indicates that construction on a building began on a specific year |
| case1_name_only | startedConstructionOn | 374 | True | Structure | YearMonthDay | indicates that a structure began construction on a specific date |
| case1_name_only | startedPerforming | 20 | True | Musician | Date | indicates that a musician began performing at a specific date |
| case1_name_only | state | 548 | True | AdministrativeDivision | AdministrativeDivision | represents the relationship where an administrative division belongs to a state |
| case1_name_only | stateOfDeath | 533 | True | Politician | State | indicates that a politician died in a specific state |
| case1_name_only | status | 146 | True | EducationalInstitution | EducationalStatus | indicates that an educational institution is recognized with a specific designation by a regulatory body |
| case1_name_only | statusGrantedBy | 254 | True | EducationalInstitution | EducationalCouncil | indicates that an educational institution receives a status designation from an educational council |
| case1_name_only | studentBody_size | 379 | True | University | StudentBody_size | represents the relationship where a university has a total student body size |
| case1_name_only | studentCount_Doctoral | 871 | True | University | StudentCount_Doctoral | indicates that a university has a specific number of doctoral students enrolled |
| case1_name_only | studentType | 871 | True |  |  |  |
| case1_name_only | students | 310 | True | University | StudentCount | indicates that a university has a total number of students |
| case1_name_only | studiesAt | 36 | True | Person | EducationalInstitution | Indicates that a person studies at an educational institution. |
| case1_name_only | succeeded | 353 | True | Politician | Politician | indicates that one politician replaces another in a political leadership role |
| case1_name_only | succeededBy | 429 | True | Politician | Politician | indicates that one politician succeeded another in a political role |
| case1_name_only | successor | 152 | True | Politician | Politician | represents the relationship where one politician succeeds another in a political role |
| case1_name_only | support | 610 | True | University | StudentPopulation | indicates that a university institution provides support services to a student body |
| case1_name_only | team | 42 | True | Player | Team | indicates that a player competes with a specific team |
| case1_name_only | teamLocation | 700 | True | Athlete | Stadium | indicates that an athletes team is based at a specific stadium |
| case1_name_only | technicalCampusAffiliation | 685 | True | EducationalInstitution | RegulatoryBody | indicates that an educational institution is affiliated with a regulatory body responsible for technical education |
| case1_name_only | technicalCampusStatus | 978 | True | EducationalInstitution | GrantStatus | represents the relationship where an educational institution is granted a specific status by a regulatory body |
| case1_name_only | timeZone | 73 | True | City | Timezone | indicates that a city operates within a specific time zone |
| case1_name_only | timezone | 61 | True | City | StandardTimezone | indicates that a city operates under a specific time zone |
| case1_name_only | toTheSouthEastOf | 107 | True | County | County | indicates that one county is located to the southeast of another county |
| case1_name_only | tookPartIn | 125 | True | Astronaut | SpaceMission | indicates that an astronaut participates in a spaceflight mission |
| case1_name_only | totalArea | 802 | True | Country | Area | indicates that a country has a specific total area |
| case1_name_only | totalNumberOfStudents | 136 | True | University | TotalNumberOfStudents | indicates that a university has a comprehensive student body count |
| case1_name_only | totalStudents | 352 | True | University | TotalStudents | indicates that a university has a total number of enrolled students |
| case1_name_only | type | 7 | True |  |  |  |
| case1_name_only | undergraduateCount | 610 | True | StudentPopulation | UndergraduateCount | represents the relationship where a student population includes a specific count of undergraduate students |
| case1_name_only | undergraduatePopulation | 702 | True | University | UndergraduatePopulation | represents the relationship where a university has a specific number of undergraduate students |
| case1_name_only | undergraduateStudentCount | 136 | True | University | UndergraduateStudentCount | indicates that a university has a specific count of undergraduate students |
| case1_name_only | undergraduateTotal | 768 | True | University | UndergraduateTotal | indicates that a university has a specific number of undergraduate students |
| case1_name_only | undergraduates | 1127 | True | EducationalInstitution | Undergraduates | indicates that an educational institution has a count of students enrolled in undergraduate programs |
| case1_name_only | uses | 313 | True | DessertFood | Cheese | indicates that a dessert food item utilizes a specific ingredient |
| case1_name_only | utcOffset | 1 | True | City | UTCOffset | indicates that a city has a UTC offset |
| case1_name_only | wasCrewMemberOf | 1089 | True | Astronaut | SpaceMission | indicates that an astronaut serves as a crew member on a space mission |
| case1_name_only | wasFoundedBy | 221 | True | BroadcastingCompany | FoundingEntity | indicates that a broadcasting company was founded by a specific founding entity |
| case1_name_only | wasInOfficeWhile | 728 | True | Individual | Presidency | indicates that an individual held a position during a specific presidency |
| case1_name_only | wasMarriedTo | 882 | True | Individual | Individual | indicates that an individual was married to another individual |
| case1_name_only | wasMemberOf | 69 | True | HistoricalFigure | SpaceMission | represents the relationship where a historical figure was part of a space mission |
| case1_name_only | wasPartOf | 639 | True | Astronaut | SpaceMission | indicates that an astronaut participates in a space mission |
| case1_name_only | weight | 46 | True | Individual | Weight | indicates that an individuals weight is measured |
| case1_name_only | westNeighbor | 501 | True | AdministrativeDivision | AdministrativeDivision | indicates that an administrative division is geographically located to the west of another |
| case1_name_only | winLeague | 128 | True | SportsTeam | League | indicates that a sports team has won a league |
| case1_name_only | winLeagueTitle | 498 | True | SportsTeam | ProfessionalLeague | indicates that a sports team has won a league title |
| case1_name_only | winningLeague | 179 | True | SportsClub | League | indicates that a sports club won a league |
| case1_name_only | wonLeague | 76 | True | SportsTeam | League | indicates that a sports team has won a league championship |
| case1_name_only | wonLeagueChampionship | 189 | True | SportsTeam | Year | indicates that a sports team won a league championship in a specific year |
| case1_name_only | wrote | 351 | True | Author | Book | represents the relationship where an author creates a book |
| case1_name_only | year | 82 | True | League | Year | indicates that a league takes place in a specific year |
| case1_name_only | yearBegunCareer | 595 | True | Musician | Year | indicates that a musician began their musical career in a specific year |
| case1_name_only | yearErected | 247 | True | HistoricalMonument | Year | represents the relationship where a monument is associated with a specific year of erection |
| case1_name_only | yearInLeague | 128 | True | SportsTeam | Year | indicates that a sports team has been in a league for a specific year |
| case1_name_only | yearInPosition | 242 | True | HistoricalFigure | YearInPosition | indicates that a historical figure served in a leadership role for a specific year |
| case1_name_only | yearOfDeath | 909 | True | Individual | Year | indicates that an individual died in a specific year |
| case1_name_only | youthClub | 101 | True | Athlete | SportsTeam | indicates that an athlete is a member of the youth team of a sports club |
| case1_name_only | youthTeam | 219 | True | Athlete | FootballClub | indicates that an athlete began their career with a specific youth football club |
| case2_name_general | CEO | 465 | True | Company | CEO | indicates that a company is led by a chief executive officer |
| case2_name_general | aboveSeaLevel | 925 | True | City | AboveSeaLevel | indicates that a city is located above a certain sea level |
| case2_name_general | absoluteMagnitude | 33 | True | Asteroid | AbsoluteMagnitude | indicates that an asteroid has a specific absolute magnitude |
| case2_name_general | absolute_magnitude | 447 | True | CelestialBody | AbsoluteMagnitude | represents the relationship where an asteroid has a specific brightness measurement |
| case2_name_general | actedIn | 111 | True | Actor | TelevisionSeries | indicates that an actor starred in a television series |
| case2_name_general | actor | 1086 | True | TelevisionShow | Actor | indicates that a show features actors in its cast |
| case2_name_general | address | 3 | True | ArchitecturalStructure | GeographicLocation | indicates that an architectural structure has a specific physical address |
| case2_name_general | adjacentCounty | 185 | True | County | County | represents the relationship where one county is geographically adjacent to another county |
| case2_name_general | affiliatedWith | 146 | True | EducationalInstitution | University | represents the relationship where an educational institution is associated with a university |
| case2_name_general | affiliation | 17 | True | Institute | University | indicates that an educational institution is associated with a university for academic purposes |
| case2_name_general | airedOn | 124 | True | TVSeries | BroadcastingCompany | indicates that a TV series is broadcasted by a specific broadcasting company |
| case2_name_general | altitudeAboveSeaLevel | 15 | True | Airport | Altitude | indicates that an airport is at a specific altitude above sea level |
| case2_name_general | anthem | 225 | True | Monarchy | NationalAnthem | represents the relationship where a monarchy has a national anthem |
| case2_name_general | apoapsis | 33 | True | Asteroid | Apoapsis | indicates that an asteroid has a specific apoapsis distance |
| case2_name_general | architect | 3 | True | ArchitecturalStructure | Architect | indicates that an architectural structure is designed by a professional architect |
| case2_name_general | are | 826 | True | Thing | Thing | indicates that a group of entities share a common identity or classification |
| case2_name_general | area | 200 | True | Country | Area | represents the relationship where a countrys geographical extent is quantified |
| case2_name_general | areaCode | 74 | True | Place | AreaCode | represents the relationship where a place is uniquely identified by a numeric area code |
| case2_name_general | assembledIn | 994 | True | Automobile | City | indicates that an automobile is manufactured in a specific city |
| case2_name_general | assemblyLineLocation | 39 | True | Vehicle | City | indicates that a vehicle was produced on an assembly line located within a city |
| case2_name_general | assemblyLocation | 520 | True | Automobile | City | indicates that an automobile is assembled in a specific city |
| case2_name_general | associatedBand | 108 | True | Musician | Band | indicates that a musician is associated with a musical group |
| case2_name_general | associatedWith | 400 | True | Musician | Musician | indicates that a musician collaborates with another artist in musical projects |
| case2_name_general | attendedSchool | 63 | True | Student | EducationalInstitution | represents the relationship where a student is enrolled in an educational institution |
| case2_name_general | author | 72 | True | Book | Author | indicates that a book is authored by an individual |
| case2_name_general | award | 154 | True | HistoricalFigure | MilitaryAward | indicates that a historical figure received a specific military award |
| case2_name_general | awarded | 599 | True | HistoricalFigure | Medal | represents the relationship where a historical figure receives a distinguished service medal |
| case2_name_general | awardedBy | 349 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure received a military award from a branch of the armed forces |
| case2_name_general | awardedTechnicalCampusStatusTo | 131 | True | GovernmentAgency | EducationalInstitution | represents the relationship where a government agency grants a technical campus status to an educational institution |
| case2_name_general | awardedTo | 154 | True | MilitaryBranch | HistoricalFigure | indicates that a military branch awards a specific historical figure a medal |
| case2_name_general | awardingBody | 615 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure is awarded by a specific military branch |
| case2_name_general | beganCareerIn | 893 | True | Musician | Date | indicates that a musician starts their professional career at a specific date |
| case2_name_general | beganMusicalCareer | 400 | True | Musician | Year | represents the relationship where a musician starts their professional music career |
| case2_name_general | beganPerforming | 376 | True | Musician | Date | indicates that a musician starts performing at a specific point in time |
| case2_name_general | birthDate | 13 | True | MilitaryPerson | Date | indicates that a military person was born on a specific date |
| case2_name_general | birthPlace | 13 | True | MilitaryPerson | City | indicates that a military person is born in a specific city |
| case2_name_general | birthYear | 34 | True | HistoricalFigure | Year | indicates that a historical figure was born in a specific year |
| case2_name_general | bodyStyle | 399 | True | Automobile | BodyStyle | represents the relationship where an automobile has a specific body style |
| case2_name_general | borderingCounty | 906 | True | County | County | indicates that a county shares borders with other counties |
| case2_name_general | born | 364 | True | Astronaut | BirthDate | indicates that an astronaut was born on a specific date |
| case2_name_general | bornIn | 4 | True | Individual | City | indicates that an individual is born in a specific city |
| case2_name_general | bornOn | 30 | True | Athlete | BirthDate | indicates that an athlete was born on a specific date |
| case2_name_general | bornWithin | 357 | True | Individual | Monarchy | indicates that an individual was born within a monarchy |
| case2_name_general | broadcastedBy | 6 | True | TVShow | BroadcastingCompany | indicates that a TV show is broadcast by a specific broadcasting company |
| case2_name_general | broughtUpBy | 250 | True | MediaCompany | AnimatedCharacter | represents the relationship where a media company is associated with a specific animated character |
| case2_name_general | buildStartDate | 965 | True | EducationalBuilding | TemporalValue | indicates that a building was constructed on a specific date |
| case2_name_general | builder | 105 | True | Locomotive | Company | represents the relationship where a locomotive is produced by a manufacturing company |
| case2_name_general | builtBetween | 150 | True | Locomotive | HistoricalPeriod | indicates that a locomotive was constructed within a specific historical time frame |
| case2_name_general | builtIn | 7 | True | HistoricalStructure | TimePeriod | indicates that a historical structure is constructed in a specific year |
| case2_name_general | builtOn | 756 | True | Structure | Date | indicates that a structure was built on a specific date |
| case2_name_general | campusLocation | 410 | True | University | Road | indicates that a university is situated on a specific road within its campus |
| case2_name_general | campusStatus | 974 | True | EducationalInstitution | CampusStatus | indicates that an educational institution has been granted a specific status by a governing body |
| case2_name_general | campus_location | 563 | True | EducationalInstitution | Address | indicates that an educational institution has a specific campus location |
| case2_name_general | canBeVaryWith | 67 | True | Dessert | DairyProduct | indicates that a dessert can be prepared with a dairy product |
| case2_name_general | categorization | 501 | True | HistoricalStructure | HistoricResource | indicates that a historical structure is recognized as a resource contributing to the significance of a district |
| case2_name_general | category | 104 | True |  |  |  |
| case2_name_general | ceremonialCounty | 830 | True | Town | CeremonialCounty | represents the relationship where a town is part of a ceremonial county |
| case2_name_general | championOf | 659 | True | SportsTeam | League | represents the relationship where a sports team is the champion of a league |
| case2_name_general | champions | 16 | True | SportsTeam | League | indicates that a sports team is the champion of a league |
| case2_name_general | championship | 920 | True | SportsClub | League | indicates that a sports club has won a specific league championship |
| case2_name_general | championships | 629 | True | SportsTeam | Number | indicates that a sports team has won a specific number of championships |
| case2_name_general | channel | 384 | True | TVSeries | BroadcastingCompany | indicates that a TV series is broadcasted on a specific television channel operated by a broadcasting company |
| case2_name_general | character | 688 | True | Actor | TelevisionSeries | indicates that an actor portrays a character in a television series |
| case2_name_general | citizens | 369 | True | Nation | Population | represents the relationship where a nation comprises a specific demographic group |
| case2_name_general | citizenship | 326 | True | Politician | Citizen | indicates that a politician holds a specific citizenship status |
| case2_name_general | city | 418 | True | EducationalInstitution | City | indicates that an educational institution is located in a specific city |
| case2_name_general | cityManager | 913 | True | City | Position | indicates that a city is led by a specific leadership role |
| case2_name_general | coach | 295 | True | Team | Coach | represents the relationship where a coach leads a sports team |
| case2_name_general | competedIn | 284 | True | SportsTeam | Season | represents the relationship where a sports team participated in a specific season |
| case2_name_general | completedOn | 190 | True | ArchitecturalStructure | CompletionDate | indicates that an architectural structure is finished on a specific completion date |
| case2_name_general | completionDate | 112 | True | Structure | Year | indicates that a building was completed on a specific year |
| case2_name_general | constructedBy | 47 | True | Structure | Architect | represents the relationship where a structure is designed by an architect |
| case2_name_general | constructionPeriod | 47 | True | Structure | Period | indicates that a structure was built within a specific time frame |
| case2_name_general | constructionStart | 361 | True | Facility | Temporal | indicates that a facilitys construction began on a specific date |
| case2_name_general | constructionStartDate | 1121 | True | EducationalBuilding | ConstructionStartDate | indicates that an educational building has a specific start date for construction |
| case2_name_general | contains | 542 | True | Dessert | DriedFruit | indicates that a dessert includes dried fruit as an ingredient |
| case2_name_general | containsAdministrativeTerritory | 129 | True | AdministrativeTerritory | AdministrativeTerritory | Indicates that an administrative territory contains another administrative territory. |
| case2_name_general | containsIngredient | 986 | True | Dish | Nutrition | indicates that a dish includes granola, shredded coconut, and raisins as nutritional ingredients |
| case2_name_general | containsSettlement | 104 | True | AdministrativeTerritory | Settlement | Indicates that an administrative territory contains a settlement such as a city or town. |
| case2_name_general | containsTeam | 284 | True | League | SportsTeam | represents the relationship where a league includes multiple sports teams |
| case2_name_general | corporateForm | 29 | True | Company | LegalForm | represents the relationship where a company has a specific legal form |
| case2_name_general | cosparId | 416 | True | SpaceMission | CosparId | represents the relationship where a space mission is uniquely identified by a COSPAR ID |
| case2_name_general | country | 3 | True | EducationalInstitution | Country | indicates that an educational institution is located in a specific country |
| case2_name_general | countryOfBirth | 356 | True | HistoricalFigure | Country | represents the relationship where a historical figure is born in a specific country |
| case2_name_general | countryOfCitizenship | 647 | True | Photographer | Nation | indicates that a photographer holds citizenship in a sovereign nation |
| case2_name_general | countryOfOrigin | 674 | True | AutomobileCompany | Nation | represents the relationship where an automobile company is founded in a particular nation |
| case2_name_general | countryOrigin | 369 | True | Sweet | Nation | indicates that a sweet dessert originates from a specific nation |
| case2_name_general | county | 7 | True | HistoricalStructure | County | indicates that a historical structure is situated within a county |
| case2_name_general | creator | 6 | True | TVShow | Creator | represents the relationship where a TV show is created by a specific creator |
| case2_name_general | crewMember | 332 | True | SpaceMission | Citizen | indicates that a space mission includes a citizen as a crew member |
| case2_name_general | currency | 24 | True | GeopoliticalEntity | MonetaryUnit | indicates that a country uses a specific currency for transactions |
| case2_name_general | currentAssemblyLocation | 697 | True | Automobile | City | indicates that an automobile is currently assembled in a specific city |
| case2_name_general | currentClub | 30 | True | Athlete | FootballClub | indicates that an athlete is currently affiliated with a football club |
| case2_name_general | currentDirector | 835 | True | EducationalInstitution | Educator | indicates that an educational institution has a current director who is an educator |
| case2_name_general | currentLeader | 699 | True | Nation | Politician | represents the relationship where a nation is led by a political leader |
| case2_name_general | currentOwner | 588 | True | EducationalBuilding | EducationalInstitution | indicates that an educational building is owned by an educational institution |
| case2_name_general | currentPosition | 156 | True | Politician | PoliticalOffice | represents the relationship where a politician holds a current political office position |
| case2_name_general | currentSenator | 476 | True | State | Politician | represents the relationship where a state is governed by a current senator |
| case2_name_general | currentTeam | 90 | True | Athlete | SportsTeam | indicates that an athlete competes for a specific sports team |
| case2_name_general | currentTenant | 730 | True | EducationalBuilding | EducationalInstitution | indicates that an educational building houses an educational institution |
| case2_name_general | currentTenants | 3 | True | ArchitecturalStructure | EducationalInstitution | indicates that an architectural structure is currently occupied by an educational institution |
| case2_name_general | currentlyPlaysFor | 95 | True | Athlete | SportsTeam | indicates that an athlete is currently affiliated with a sports team |
| case2_name_general | cylinderCount | 878 | True | Locomotive | CylinderCount | indicates that a locomotive has a specific number of cylinders |
| case2_name_general | dateOfBirth | 25 | True | Individual | BirthDate | indicates that an individual has a specific birth date |
| case2_name_general | dateOfDeath | 173 | True | Individual | DeathDate | indicates that an individual died on a specific date |
| case2_name_general | dateOfRetirement | 154 | True | HistoricalFigure | RetirementDate | indicates that a historical figure retired on a specific date |
| case2_name_general | dateOfRole | 633 | True | HistoricalFigure | HistoricalYear | indicates that a historical figure held a role in a specific year |
| case2_name_general | deathCause | 640 | True | Individual | Death | indicates that an individuals death is caused by a natural or medical condition |
| case2_name_general | deathDate | 93 | True | Individual | DeathDate | indicates that an individual has a specific death date |
| case2_name_general | deathPlace | 28 | True | Politician | Nation | indicates that a politician died in a specific nation |
| case2_name_general | debutTeam | 425 | True | Player | Team | indicates that a player made their initial appearance for a specific team |
| case2_name_general | degree | 477 | True | EducationalInstitution | Degree | indicates that an educational institution awarded a specific degree |
| case2_name_general | designatedTechnicalCampusStatusTo | 143 | True | Council | Institute | indicates that a council formally recognizes a technical education institution as a campus |
| case2_name_general | diedIn | 4 | True | Individual | Country | indicates that an individual dies in a specific country |
| case2_name_general | directedBy | 643 | True | EducationalInstitution | EducationalLeader | indicates that an educational institution is led by a person in charge of academic affairs |
| case2_name_general | direction | 365 | True | AdministrativeDivision | GeographicalDirection | indicates that a territorial division is geographically positioned relative to another |
| case2_name_general | director | 131 | True | EducationalInstitution | Educator | represents the relationship where an educational institution is led by an educator |
| case2_name_general | discovered | 182 | True | Astronomer | AstronomicalBody | indicates that an astronomer identifies a celestial body |
| case2_name_general | discoveredBy | 33 | True | Asteroid | Astronomer | indicates that an asteroid is identified by an astronomer |
| case2_name_general | discoveryDate | 33 | True | Asteroid | Date | indicates that an asteroids discovery is recorded with a specific date |
| case2_name_general | doctoralStudents | 66 | True | University | DoctoralStudents | indicates that a university has a specific number of students enrolled in doctoral programs |
| case2_name_general | draftPick | 518 | True | Athlete | DraftPick | indicates that an athlete is selected as a draft pick |
| case2_name_general | draftPickNumber | 1057 | True | Athlete | DraftPickNumber | indicates that an athlete is assigned a draft pick number |
| case2_name_general | earnings | 85 | True | Company | Earnings | indicates that a company generates financial income over a year |
| case2_name_general | eat | 790 | True | Dessert | Type | indicates that a dessert is consumed as a type of food |
| case2_name_general | educates | 257 | True | University | StudentPopulation | indicates that a university enrolls a total number of students |
| case2_name_general | education | 53 | True | HistoricalFigure | Degree | indicates that a historical figure has earned a formal academic degree |
| case2_name_general | elevationAboveSeaLevel | 41 | True | Airport | ElevationAboveSeaLevel | indicates that an airport has a specific elevation above sea level measurement |
| case2_name_general | endDateConstruction | 946 | True | Structure | Temporal | indicates that a building was completed at a specific point in time |
| case2_name_general | endedManufacturingOf | 325 | True | Automaker | AutomobileModel | indicates that an automaker ceases production of a specific vehicle model |
| case2_name_general | engine | 350 | True | Locomotive | Engine | indicates that a locomotive is equipped with a particular type of engine |
| case2_name_general | engineConfiguration | 749 | True | Locomotive | EngineConfiguration | indicates that a locomotive employs a particular engine configuration |
| case2_name_general | engineType | 65 | True |  |  |  |
| case2_name_general | enrollment | 70 | True | University | StudentCount | represents the relationship where a university has a specific number of students enrolled |
| case2_name_general | epoch | 64 | True | Asteroid | Time | represents the relationship where an asteroid reaches a specific epoch in its orbit |
| case2_name_general | epochDate | 958 | True | CelestialBody | Date | indicates that a celestial body has a specific reference date |
| case2_name_general | erectedIn | 638 | True | Monument | State | indicates that a monument is erected in a specific state |
| case2_name_general | established | 48 | True | HistoricalMonument | TimePeriod | indicates that a historical monument is founded in a specific year |
| case2_name_general | establishedIn | 146 | True | EducationalInstitution | Year | indicates that an educational institution was founded in a specific year |
| case2_name_general | establishmentYear | 315 | True | HistoricalStructure | TimePeriod | indicates that a historical structure was founded in a specific year |
| case2_name_general | ethnicGroup | 4 | True | Country | Group | represents the relationship where a country has a specific ethnic group |
| case2_name_general | ethnonym | 735 | True | Nation | EthnicGroup | represents the relationship where a nation has an ethnonym |
| case2_name_general | extinctionDate | 558 | True | AutomobileBrand | Year | represents the relationship where an automobile brand ceased operations on a specific year |
| case2_name_general | firstAired | 6 | True | TVShow | EventDate | indicates that a TV show marks its premiere on a specific date |
| case2_name_general | firstAiredOn | 672 | True | TVSeries | EventDate | indicates that a TVSeries has a specific event date of its premiere |
| case2_name_general | firstAppearance | 260 | True | Film | AnimatedCharacter | represents the relationship where a film features its initial appearance of an animated character |
| case2_name_general | firstAppearedAsFilmCharacterIn | 779 | True | FilmCharacter | Film | represents the relationship where a characters first appearance in a film is specified |
| case2_name_general | firstAppearedIn | 824 | True | AnimatedCharacter | Film | represents the relationship where an animated characters debut is in a movie |
| case2_name_general | firstBroadcast | 250 | True | AnimatedCharacter | EventDate | indicates that an animated character had its first broadcast on a specific date |
| case2_name_general | firstProducedIn | 199 | True | Automobile | Year | indicates that an automobile was first manufactured in a specific year |
| case2_name_general | firstProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was first manufactured in a specific year |
| case2_name_general | followedBy | 241 | True | Book | Book | indicates that one book series continues another in a narrative sequence |
| case2_name_general | follows | 585 | True | Book | Book | indicates that one book comes after another in a series |
| case2_name_general | foodServedAsDessert | 811 | True | Nation | Dessert | indicates that a nation serves a specific dessert as a dessert |
| case2_name_general | formerClub | 616 | True | Player | FootballClub | represents the relationship where a player was previously affiliated with a football club |
| case2_name_general | formerTeam | 186 | True | Player | Team | represents the relationship where a player was formerly part of a team |
| case2_name_general | formerlyPlayedWith | 318 | True | Athlete | SportsTeam | indicates that an athlete previously played for a sports team |
| case2_name_general | foundIn | 19 | True | DessertFood | Country | represents the relationship where a dessert food item is located within a specific country |
| case2_name_general | founded | 114 | True | Company | Date | indicates that a company was established on a specific date |
| case2_name_general | foundedBy | 120 | True | Company | Founder | represents the relationship where a company is initiated by a person |
| case2_name_general | founder | 62 | True | Company | Founder | represents the relationship where a company is initiated and managed by a founder |
| case2_name_general | founding | 691 | True | City | HistoricalFigure | represents the relationship where a city is founded by a historical figure |
| case2_name_general | foundingDate | 22 | True | PharmaceuticalCompany | FoundingDate | indicates that a pharmaceutical company was established on a specific founding date |
| case2_name_general | foundingEntity | 221 | True | BroadcastingCompany | FoundingEntity | represents the relationship where a broadcasting company is established by a founding entity |
| case2_name_general | foundingPerson | 831 | True | Company | Founder | indicates that a company was founded by a specific person |
| case2_name_general | foundingPlace | 114 | True | Company | City | indicates that a company was founded in a specific city |
| case2_name_general | from | 936 | True | Musician | Thing | indicates that a musician is associated with a specific geographic entity |
| case2_name_general | fullAddress | 392 | True | Institute | Address | indicates that an institute has a specific full physical address |
| case2_name_general | fullName | 203 | True | State | Name | indicates that a state has a formal name |
| case2_name_general | full_name | 246 | True | SportsTeam | SportsTeam | indicates that a sports team has a formal name |
| case2_name_general | gaveStatusBy | 857 | True | EducationalInstitution | EducationalAuthority | indicates that an educational institution is granted a status by an educational authority |
| case2_name_general | gaveTechnicalCampusStatusTo | 392 | True | Council | Institute | indicates that a council grants a specific status to a technical education institution |
| case2_name_general | genre | 91 | True | TV_series | Series | indicates that a TV series belongs to a specific series category |
| case2_name_general | governingBody | 748 | True | City | Position | indicates that a city is governed by a specific leadership position |
| case2_name_general | governmentForm | 1036 | True | StateFormOfGovernment | UnitaryState | indicates that a state form of government is characterized by a centralized system of governance |
| case2_name_general | governmentType | 1 | True |  |  |  |
| case2_name_general | graduatedFrom | 512 | True | HistoricalFigure | EducationalInstitution | indicates that a historical figure received a degree from an educational institution |
| case2_name_general | graduatedIn | 477 | True | HistoricalFigure | Year | indicates that a historical figure graduated in a specific year |
| case2_name_general | graduationYear | 242 | True | HistoricalFigure | GraduationYear | indicates that a historical figure completed an educational program in a specific year |
| case2_name_general | ground | 16 | True | Stadium | SportsTeam | indicates that a stadium hosts a sports team |
| case2_name_general | hadCampusIn | 492 | True | University | City | indicates that a university had its campus within a specific city |
| case2_name_general | has | 48 | True | AdministrativeDivision | AdministrativeDivision | indicates that a territorial division contains another territorial division |
| case2_name_general | hasBird | 282 | True | State | Species | represents the relationship where a state is associated with a specific bird species |
| case2_name_general | hasFood | 945 | True | Nation | Dessert | indicates that a nation includes a specific type of food in its culinary offerings |
| case2_name_general | hasIngredient | 929 | True | Dish | Ingredient | represents the relationship where a dish has a variety of ingredients |
| case2_name_general | hasItem | 171 | True | UrbanCenter | SweetFood | represents the relationship where an urban center has another specific type of sweet food item |
| case2_name_general | hasMember | 376 | True | Band | Musician | represents the relationship where a band includes a musician as one of its members |
| case2_name_general | hasNativeBird | 505 | True | State | Bird | represents the relationship where a state is home to a specific native bird species |
| case2_name_general | hasOfficial | 493 | True | State | Official | represents the relationship where a state appoints an official to lead its administration |
| case2_name_general | hasPart | 727 | True | GeographicArea | GeographicArea | represents the relationship where one geographic area contains another |
| case2_name_general | hasPopulationDensity | 669 | True | Country | PopulationDensity | represents the relationship where a country has a specific population density |
| case2_name_general | hasSenator | 789 | True | State | Politician | represents the relationship where a state has a senator |
| case2_name_general | hasSubsidiary | 85 | True | Company | Subsidiary | represents the relationship where a company maintains a subsidiary organization |
| case2_name_general | hasTeam | 524 | True | ProfessionalLeague | SportsClub | represents the relationship where a professional league has a team belonging to a sports club |
| case2_name_general | hasUndergraduateStudents | 462 | True | University | UndergraduateStudents | indicates that a university enrolls a specific number of undergraduate students |
| case2_name_general | hasVariation | 985 | True | Dessert | Dessert | indicates that a dessert has a variation of another dessert |
| case2_name_general | headquarteredIn | 386 | True | University | City | indicates that a university is geographically located within a specific city |
| case2_name_general | headquarters | 111 | True | TelevisionNetwork | Headquarters | indicates that a television network has its administrative center in a specific building |
| case2_name_general | headquartersLocation | 99 | True | AirlineCompany | City | indicates that an airline company has its headquarters in a city |
| case2_name_general | height | 90 | True | Athlete | Height | indicates that an athlete has a specific height measurement |
| case2_name_general | heldOfficeWhile | 862 | True | Politician | Politician | indicates that a politician held office during the tenure of another politician |
| case2_name_general | homeGround | 88 | True | SportsTeam | Stadium | indicates that a sports team has a designated home ground venue |
| case2_name_general | icaoIdentifier | 355 | True | Aerodrome | ICAOIdentifier | indicates that an aerodrome is assigned a unique ICAO identifier |
| case2_name_general | icaoLocationIdentifier | 14 | True | Aerodrome | ICAOIdentifier | represents the relationship where an aerodrome is assigned a unique ICAO identifier |
| case2_name_general | inOfficeWith | 344 | True | Politician | Politician | indicates that two politicians held office simultaneously |
| case2_name_general | industry | 187 | True | Company | BuildingMaterials | represents the relationship where a company operates within a specific industry category |
| case2_name_general | ingredient | 147 | True | MexicanDessert | DairyProduct | indicates that a Mexican dessert contains a dairy-based ingredient |
| case2_name_general | ingredients | 24 | True | DessertFood | FoodIngredients | indicates that a dessert food is composed of specific ingredients |
| case2_name_general | inhabit | 790 | True | Nation | Country | represents the relationship where a nation is inhabited by a specific country |
| case2_name_general | inhabitant | 24 | True | GeopoliticalEntity | HumanPopulation | represents the relationship where a country is populated by its inhabitants |
| case2_name_general | inhabitants | 67 | True | Country | Population | indicates that a country is inhabited by a population |
| case2_name_general | inhabitedBy | 485 | True | Mexico | HumanPopulation | represents the relationship where the inhabitants of Mexico are the Mexicans |
| case2_name_general | is | 826 | True | Thing | Thing | represents the relationship where an entity belongs to a specific category |
| case2_name_general | isA | 19 | True |  |  |  |
| case2_name_general | isAffiliatedTo | 133 | True |  |  |  |
| case2_name_general | isAffiliatedWith | 198 | True |  |  |  |
| case2_name_general | isAnEthnicGroup | 1034 | True |  |  |  |
| case2_name_general | isAssociatedWith | 131 | True |  |  |  |
| case2_name_general | isBasedAt | 345 | True | BroadcastingCompany | Building | indicates that a broadcasting company operates from a physical workplace |
| case2_name_general | isBasedIn | 51 | True | Airport | City | indicates that an airport is geographically located within a city |
| case2_name_general | isCapitalOf | 669 | True | Country | Country | represents the relationship where a country is the capital of itself |
| case2_name_general | isCategorizedAs | 48 | True | HistoricalMonument | HistoricProperty | indicates that a historical monument is classified as a significant property |
| case2_name_general | isChampion | 82 | True | SportsClub | BooleanValue | indicates that a sports club is the champion of a league |
| case2_name_general | isChampionOf | 284 | True | SportsTeam | League | indicates that a sports team won a championship in a league competition |
| case2_name_general | isChiefOf | 866 | True | HistoricalFigure | AerospaceAgency | indicates that a historical figure leads an aerospace agency |
| case2_name_general | isContributing_Property | 873 | True | HistoricalMonument | TrueValue | represents the relationship where a historical monument is considered significant or contributing to a site |
| case2_name_general | isDessert | 791 | True | SweetDish | LogicalValue | represents the relationship where a dessert dish is classified as a dessert |
| case2_name_general | isEthnicGroup | 427 | True | Community | Nation | represents the relationship where an ethnic group is part of a national entity |
| case2_name_general | isFoundationPlace | 499 | True | FoundationPlace | FoundationPlace | indicates that a FoundationPlace serves as the origin or basis of another FoundationPlace |
| case2_name_general | isFrom | 725 | True | Individual | Thing | indicates that an individual is from a specific entity |
| case2_name_general | isHomeTo | 466 | True | EducationalBuilding | EducationalInstitution | indicates that an educational building houses an educational institution |
| case2_name_general | isInhabitedBy | 860 | True | Nation | Population | indicates that a nation is populated by a specific demographic group |
| case2_name_general | isLeaderOf | 303 | True | Politician | Thing | indicates that a politician holds leadership over a specific entity |
| case2_name_general | isLocatedIn | 48 | True | HistoricalMonument | Municipality | indicates that a historical monument is located within a populated place |
| case2_name_general | isLocationOf | 969 | True | Country | Population | represents the relationship where a country is the location of its population |
| case2_name_general | isManagedBy | 367 | True | City | GovernmentPosition | indicates that a city is managed by a specific government position |
| case2_name_general | isMemberOf | 50 | True | Musician | Band | represents the relationship where a musician is part of a musical group |
| case2_name_general | isNear | 744 | True | HistoricalMonument | County | indicates that a historical monument is located near another county |
| case2_name_general | isPartOf | 1 | True | City | State | indicates that a city is administratively part of a state |
| case2_name_general | isServedAs | 305 | True | FoodItem | MealComponent | represents the relationship where a food item is part of a meal course |
| case2_name_general | isServedBy | 354 | True | Autodrome | Aerodrome | indicates that an autodrome is served by another location |
| case2_name_general | isStarOf | 345 | True | Actor | TVShow | indicates that an actor performs in a television show |
| case2_name_general | isType | 1077 | True |  |  |  |
| case2_name_general | isWestOf | 836 | True | City | County | indicates that a city is located west of a county |
| case2_name_general | jobTitle | 771 | True | MilitaryPerson | MilitaryRole | indicates that a military person holds a specific combat leadership role |
| case2_name_general | keyPerson | 461 | True | PharmaceuticalCompany | Executive | represents the relationship where a pharmaceutical company is led by a high-ranking executive |
| case2_name_general | keyPersonAt | 1113 | True | KeyPerson | MassMediaCompany | indicates that a key person holds a significant role within a mass media company |
| case2_name_general | keyPersonFor | 609 | True | KeyPerson | Company | indicates that a key person oversees a company |
| case2_name_general | keyPersonIn | 818 | True | KeyPerson | Company | indicates that a key person holds a significant role within a company organization |
| case2_name_general | language | 340 | True | Nation | ModernLanguage | represents the relationship where a nation employs a modern form of a language |
| case2_name_general | lastAired | 366 | True | TVSeries | EventDate | indicates that a TV series concludes on a specific event date |
| case2_name_general | lastAiredOn | 167 | True | Program | Date | indicates that a program was last aired on a specific date |
| case2_name_general | lastProducedIn | 199 | True | Automobile | Year | indicates that an automobile was last manufactured in a specific year |
| case2_name_general | lastProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was last manufactured in a specific year |
| case2_name_general | leader | 196 | True | City | Politician | represents the relationship where a city is governed by a political leader |
| case2_name_general | leaderName | 251 | True | City | Leader | represents the relationship where a city is led by a specific person |
| case2_name_general | leaderTitle | 1 | True | City | LeaderTitle | indicates that a city has a leadership role title |
| case2_name_general | leadershipTitle | 280 | True | Country | LeadershipRole | indicates that a country has a specific title for its leadership role |
| case2_name_general | league | 16 | True | SportsTeam | League | indicates that a sports team competes in a specific league |
| case2_name_general | leagueTitle | 975 | True | SportsTeam | League | indicates that a sports team competes in a specific league title |
| case2_name_general | length | 2 | True | Locomotive | Length | represents the relationship where a locomotives physical dimension is defined |
| case2_name_general | locatedAboveSeaLevel | 83 | True | Airport | Altitude | indicates that an airport is at a specific elevation above sea level |
| case2_name_general | locatedAt | 643 | True | EducationalInstitution | Address | represents the specific address or location of an educational institution |
| case2_name_general | locatedIn | 346 | True | HistoricalMonument | County | indicates that a historical monument is geographically located within a county |
| case2_name_general | locatedInAdministrativeTerritory | 43 | True | Location | AdministrativeTerritory | Indicates that a location is located within a specific administrative territorial entity. |
| case2_name_general | locatedInCountry | 73 | True | Location | Country | Indicates that a location is located in a country. |
| case2_name_general | location | 0 | True | Company | City | represents the relationship where a companys physical presence is located within a city |
| case2_name_general | locationElevation | 56 | True | Aerodrome | Elevation | indicates that an aerodrome has a specific elevation above sea level |
| case2_name_general | locationInTimezone | 852 | True | City | Zone | indicates that a city is located in a specific time zone |
| case2_name_general | locationOf | 498 | True | Stadium | SportsTeam | indicates that a stadium is the home ground of a sports team |
| case2_name_general | locationOfDeath | 173 | True | Country | Country | indicates that a country is the location of an individual's death |
| case2_name_general | locationOfFounding | 808 | True | Company | City | indicates that a company was founded in a specific city location |
| case2_name_general | locationOfManufacture | 580 | True | Automobile | City | indicates that an automobile is manufactured in a specific city |
| case2_name_general | locationOfOccurrence | 449 | True | Ingredient | Country | indicates that an ingredient is found within a specific country |
| case2_name_general | locationOfProduction | 199 | True | Automobile | City | indicates that an automobile was produced in a specific city |
| case2_name_general | locationRelation | 78 | True | County | SpatialRelation | represents the relationship where a county is situated relative to another county in a north-south direction |
| case2_name_general | longName | 174 | True | Nation | OfficialName | represents the relationship where a nations long name corresponds to its official name |
| case2_name_general | magnitude | 739 | True | Asteroid | Magnitude | indicates that an asteroid has a numerical measure of its brightness |
| case2_name_general | mainDishType | 421 | True |  |  |  |
| case2_name_general | mainIngredient | 381 | True | BakeryItem | DairyProduct | indicates that a bakery item has dairy products as main ingredients |
| case2_name_general | mainProduct | 27 | True | Company | Software | represents the relationship where a company specializes in creating software products |
| case2_name_general | makes | 22 | True | PharmaceuticalCompany | Medicine | indicates that a pharmaceutical company produces medical products |
| case2_name_general | makesProduct | 627 | True | Company | Software | indicates that a company produces software products |
| case2_name_general | manager | 5 | True | SportsTeam | Manager | indicates that a sports team is led by a manager |
| case2_name_general | managerOfCurrentTeam | 572 | True | Athlete | Manager | indicates that an athlete has a manager for their current team |
| case2_name_general | managerTitle | 29 | True | Company | ManagerTitle | indicates that a company is managed by a specific title |
| case2_name_general | manages | 192 | True | Athlete | Coach | represents the relationship where an athlete oversees a coaching role |
| case2_name_general | manufacturer | 574 | True | Locomotive | Company | indicates that a locomotive is produced by a manufacturing company |
| case2_name_general | marriage | 640 | True | Individual | Individual | indicates that two individuals are legally or socially united in marriage |
| case2_name_general | member | 343 | True | Band | Musician | indicates that a band has a musician as one of its members |
| case2_name_general | memberOf | 30 | True | Athlete | YouthTeam | indicates that an athlete is a member of a youth sports team |
| case2_name_general | mission | 25 | True | Individual | SpaceMission | indicates that an individual participates in a spaceflight mission |
| case2_name_general | monumentCategory | 955 | True |  |  |  |
| case2_name_general | movedTo | 1161 | True | Company | Country | indicates that a company relocated to a specific country |
| case2_name_general | municipality | 7 | True | HistoricalStructure | City | indicates that a historical structure is located within a city |
| case2_name_general | name | 479 | True | Stadium | Stadium | indicates that a stadium has a specific name |
| case2_name_general | nationalAnthem | 269 | True | Government | NationalAnthem | represents the relationship where a government holds a national anthem |
| case2_name_general | nationality | 11 | True | Individual | Country | indicates that an individual belongs to a specific country |
| case2_name_general | nativeOf | 477 | True | State | Bird | indicates that a state is the native home of a bird species |
| case2_name_general | nearbyPlace | 966 | True | County | County | indicates that a county has another county nearby |
| case2_name_general | neighbor | 403 | True | State | County | indicates that a state shares administrative boundaries with another county |
| case2_name_general | netIncome | 149 | True | Company | NetIncome | represents the relationship where a companys net income is a specific financial metric |
| case2_name_general | network | 91 | True | TV_series | BroadcastingCompany | indicates that a TV series is broadcasted by a broadcasting company |
| case2_name_general | nickname | 88 | True | SportsTeam | Nickname | represents the relationship where a sports team has a distinctive nickname |
| case2_name_general | northNeighbour | 165 | True | County | County | indicates that a county is geographically located north of another county |
| case2_name_general | numberOfAcademicStaff | 556 | True | EducationalInstitution | Number | indicates that an educational institution employs a specific number of academic staff |
| case2_name_general | numberOfDoctoralStudents | 900 | True | University | Number | indicates that a university has a specific number of doctoral students |
| case2_name_general | numberOfEmployees | 114 | True | Company | Number | indicates that a company has a specific number of employees |
| case2_name_general | numberOfMembers | 5 | True | SportsTeam | Number | indicates that a sports team has a specific number of members |
| case2_name_general | numberOfPages | 72 | True | Book | Pages | indicates that a book has a specific number of pages |
| case2_name_general | numberOfPostgraduateStudents | 492 | True | University | PostgraduateStudentsQuantity | indicates that a university has a specific number of postgraduate students enrolled |
| case2_name_general | numberOfStaffMembers | 448 | True | University | NumberOfStaffMembers | indicates that a university has a specific number of staff members |
| case2_name_general | numberOfStudents | 66 | True | University | StudentCount | indicates that a university has a total count of students including various levels and staff members |
| case2_name_general | numberOfUndergraduateStudents | 118 | True | University | Number | indicates that a university has a specific count of undergraduate students |
| case2_name_general | occupation | 13 | True | MilitaryPerson | MilitaryOccupation | indicates that a military person holds a specific military role |
| case2_name_general | offersProduct | 525 | True | MediaCompany | Software | represents the relationship where a media company provides software products |
| case2_name_general | offersServices | 737 | True | Company | WebServices | represents the relationship where a company provides services related to the World Wide Web |
| case2_name_general | offersSport | 556 | True | EducationalInstitution | Activity | indicates that an educational institution offers a specific sport |
| case2_name_general | officeHolder | 28 | True | Politician | Politician | indicates that a politician holds a position equivalent to another politician |
| case2_name_general | officeStartDate | 885 | True | HistoricalFigure | Year | indicates that a historical figure began holding an administrative role in a specific year |
| case2_name_general | officialLanguage | 183 | True | State | OfficialLanguage | represents the relationship where a state has a primary official language |
| case2_name_general | operatedBy | 10 | True | Airbase | MilitaryBranch | indicates that an airbase is managed by a military branch |
| case2_name_general | operates | 51 | True | Airline | Airport | indicates that an airline manages an airport facility |
| case2_name_general | operatingArea | 802 | True | Company | Country | represents the relationship where a company operates within a specific country |
| case2_name_general | operatingOrganisationFor | 463 | True |  |  |  |
| case2_name_general | operatingOrganization | 132 | True | Aerodrome | OperatingOrganization | represents the relationship where an aerodrome is managed by an operating organization |
| case2_name_general | operator | 40 | True | Airport | AeronauticsCompany | indicates that an airport is managed by an aeronautics company |
| case2_name_general | orbitalPeriod | 33 | True | Asteroid | OrbitalPeriod | indicates that an asteroid has a specific orbital period |
| case2_name_general | orbital_period | 135 | True | Asteroid | OrbitalPeriod | indicates that an asteroid has a duration for its orbit around its primary body |
| case2_name_general | origin | 630 | True | Musician | City | indicates that a musician originates from a specific city |
| case2_name_general | originCountry | 108 | True | Musician | Nation | indicates that a musician originates from a sovereign state |
| case2_name_general | otherTeam | 395 | True | Athlete | SportsTeam | indicates that an athlete is associated with another sports team |
| case2_name_general | ownedBuilding | 588 | True | EducationalInstitution | EducationalBuilding | indicates that an educational institution owns a specific educational building |
| case2_name_general | ownedBy | 374 | True | Structure | EducationalInstitution | indicates that a structure is owned by an educational institution |
| case2_name_general | owner | 38 | True | EducationalFacility | EducationalInstitution | indicates that an educational institution owns a specific facility |
| case2_name_general | owns | 9 | True | EducationalInstitution | EducationalFacility | indicates that an educational institution possesses a specific educational facility |
| case2_name_general | parent | 111 | True | Actor | Daughter | indicates that an actor has a daughter |
| case2_name_general | parentCompany | 609 | True | Company | Company | represents the relationship where a company is the parent entity of another company |
| case2_name_general | partOfMission | 897 | True | MilitaryPerson | SpaceMission | indicates that a military person is part of a specific space mission |
| case2_name_general | participatedIn | 924 | True | MilitaryPerson | SpaceMission | indicates that a military person participated in a space mission |
| case2_name_general | people | 1093 | True | Region | Nationality | represents the relationship where a region is inhabited by a specific nationality |
| case2_name_general | peopleName | 171 | True | Nation | PeopleGroup | represents the relationship where a nation has a specific name for its people |
| case2_name_general | periapsis | 49 | True | Asteroid | Periapsis | indicates that an asteroid has a specific periapsis distance |
| case2_name_general | placeOfBirth | 141 | True | Individual | BirthPlace | indicates that an individual was born in a specific geographic location |
| case2_name_general | placeOfDeath | 154 | True | HistoricalFigure | State | indicates that a historical figure died in a specific state |
| case2_name_general | placeOfOrigin | 52 | True | Individual | State | indicates that an individuals place of origin is within a specific state |
| case2_name_general | placeOfUpbringing | 722 | True | Individual | Country | indicates that an individual grew up in a sovereign country |
| case2_name_general | playIn | 293 | True | SportsTeam | League | indicates that a sports team competes in a league organized by a governing body |
| case2_name_general | playInLeague | 319 | True | SportsTeam | ProfessionalLeague | represents the relationship where a sports team is affiliated with a professional sports league |
| case2_name_general | playedBy | 430 | True | League | SportsTeam | indicates that a league is contested by multiple sports teams |
| case2_name_general | playedFor | 95 | True | Athlete | SportsTeam | indicates that an athlete competes for a sports team |
| case2_name_general | playedIn | 179 | True | SportsClub | Year | indicates that a sports club participated in a competition in a specific year |
| case2_name_general | playedInLeague | 629 | True | SportsTeam | League | represents the relationship where a sports team competes in a league |
| case2_name_general | playedInSeason | 76 | True | SportsTeam | Year | indicates that a sports team competes in a specific season |
| case2_name_general | playedWith | 20 | True | Musician | Band | indicates that a musician is a member of a band |
| case2_name_general | playground | 1101 | True | SportsClub | Stadium | indicates that a sports club has a designated sports facility |
| case2_name_general | playsInstrument | 50 | True | Musician | MusicalInstrument | indicates that a musician uses a specific musical instrument in their performances |
| case2_name_general | playsMusic | 607 | True | Musician | Genre | indicates that a musician performs music within a specific genre |
| case2_name_general | population | 1 | True | City | Population | indicates that a city has a total population count |
| case2_name_general | populationDensity | 1 | True | City | PopulationDensity | indicates that a city has a specific population density |
| case2_name_general | populationMetro | 31 | True | City | Population | indicates that a city has a total population count within its metropolitan area |
| case2_name_general | populationTotal | 273 | True | DemographicEntity | Population | represents the relationship where a countrys total population is specified |
| case2_name_general | position | 217 | True | Politician | LegislativeOffice | indicates that a politician holds a legislative office position |
| case2_name_general | postalCode | 296 | True | Village | PostalCode | represents the relationship where a village is linked to a standardized alphanumeric postal code |
| case2_name_general | postalCodeRange | 561 | True | City | PostalCodeRange | represents the relationship where a citys postal codes are grouped within a specific range |
| case2_name_general | postgraduateStudentCount | 521 | True | University | PostgraduateStudentCount | represents the relationship where a university has a specific number of post-graduate students |
| case2_name_general | postgraduateStudents | 193 | True | University | PostgraduateStudentsCount | indicates that a university has a specific number of postgraduate students enrolled |
| case2_name_general | postgraduates | 1127 | True | EducationalInstitution | Postgraduates | indicates that an educational institution has a count of students enrolled in postgraduate programs |
| case2_name_general | powerType | 2 | True |  |  |  |
| case2_name_general | precedes | 100 | True | FantasyWork | FantasyWork | indicates that one work of fiction follows another in a chronological order |
| case2_name_general | prequelOf | 396 | True | Book | Book | represents the relationship where one book is a prequel to another |
| case2_name_general | president | 691 | True | EducationalInstitution | Individual | indicates that an educational institution is led by an individual holding a leadership position |
| case2_name_general | presidentDuringService | 326 | True | Politician | Politician | indicates that a politician served during the presidency of another politician |
| case2_name_general | presidentDuringTenure | 311 | True | Politician | Politician | represents the relationship where a politician serves as president during a specific tenure |
| case2_name_general | presidentServedUnder | 429 | True | Politician | Politician | represents the relationship where a politician served under a specific president |
| case2_name_general | previousChampion | 88 | True | SportsTeam | SportsTeam | indicates that a sports team has previously won a championship |
| case2_name_general | previousChampions | 419 | True | League | SportsClub | represents the relationship where a league has previously been won by a sports club |
| case2_name_general | previousPosition | 914 | True | HistoricalFigure | ProfessionalRole | indicates that a historical figure held a previous professional role |
| case2_name_general | previousRole | 90 | True | Athlete | TeamRole | indicates that an athlete held a specific role in a previous team |
| case2_name_general | previousTeam | 90 | True | Athlete | SportsTeam | indicates that an athlete previously played for a different sports team |
| case2_name_general | previouslyLedBy | 1097 | True | City | Politician | represents the relationship where a city was previously governed by a political leader |
| case2_name_general | produced | 208 | True | AutomotiveCompany | Automobile | indicates that an automotive company manufactures a specific vehicle model |
| case2_name_general | produces | 27 | True | Company | Software | indicates that a company manufactures or develops software products |
| case2_name_general | productionEndYear | 60 | True | Automobile | Year | indicates that an automobile ends production in a specific year |
| case2_name_general | productionEnded | 855 | True | Automobile | Thing | represents the relationship where an automobile production ends at a particular point in time |
| case2_name_general | productionLocation | 137 | True | Automobile | State | indicates that an automobile is manufactured in a specific state |
| case2_name_general | productionPeriod | 426 | True | Locomotive | ProductionPeriod | indicates that a locomotive was produced within a specific time frame |
| case2_name_general | productionStartYear | 60 | True | Automobile | Year | indicates that an automobile begins production in a specific year |
| case2_name_general | propertyOf | 244 | True | ArchitecturalStructure | University | indicates that a university owns the architectural structure |
| case2_name_general | publicationDate | 253 | True | FantasyNovel | PublicationDate | represents the relationship where a fantasy novel has a specific release date |
| case2_name_general | published | 253 | True | Publisher | FantasyNovel | indicates that a publisher releases a fantasy novel into the market |
| case2_name_general | publisher | 100 | True | FantasyWork | Publisher | indicates that a publisher is responsible for the publication of a work of fiction |
| case2_name_general | receivedAward | 53 | True | HistoricalFigure | MilitaryAward | indicates that a historical figure has been awarded a military honor |
| case2_name_general | region | 26 | True | Dessert | GeographicArea | indicates that a dessert is associated with a specific geographic region |
| case2_name_general | relateto | 7 | True | County | County | indicates that two counties are geographically adjacent to each other |
| case2_name_general | relationToOther | 688 | True | Actor | Daughter | represents the relationship where an actor is the father of another person |
| case2_name_general | relationTo_Alan_Shepard | 840 | True | EducationalInstitution | Graduation | represents the relationship where an educational institution is associated with an individual completing an educational program |
| case2_name_general | releaseDate | 172 | True | Book | ReleaseDate | indicates that a book was released on a specific date |
| case2_name_general | represented | 217 | True | Politician | State | indicates that a politician represents a specific state |
| case2_name_general | requires | 860 | True | SweetDish | FoodItem | indicates that a dessert requires a specific food item as an ingredient |
| case2_name_general | retiredOn | 69 | True | HistoricalFigure | Date | indicates that a historical figure retired on a specific date |
| case2_name_general | retirementDate | 615 | True | HistoricalFigure | RetirementDate | indicates that a historical figure retires on a specific date |
| case2_name_general | revenue | 117 | True | Company | Revenue | represents the relationship where a company generates a specific amount of income |
| case2_name_general | role | 332 | True | Citizen | Professional | indicates that a citizen holds a specific professional role |
| case2_name_general | rotationPeriod | 33 | True | Asteroid | RotationPeriod | indicates that an asteroid has a specific rotation period |
| case2_name_general | rotation_period | 103 | True | Planet | Duration | indicates that a planet completes one rotation in a given duration |
| case2_name_general | rotationalPeriod | 109 | True | Asteroid | RotationalPeriod | indicates that an asteroid rotates on its axis in a specific amount of time |
| case2_name_general | runwayLength | 10 | True | Airbase | RunwayLength | indicates that an airbase has a specific runway length |
| case2_name_general | runwayMaterial | 249 | True | Aerodrome | Concrete | represents the relationship where an aerodrome runway is constructed with concrete |
| case2_name_general | runwayName | 45 | True | Airport | RunwayName | indicates that an airport has a unique runway name |
| case2_name_general | runwaySurface | 122 | True | Aerodrome | Concrete | indicates that an aerodrome has a runway surface made of concrete |
| case2_name_general | runwaySurfaceMaterial | 502 | True | Aerodrome | ConstructionMaterial | indicates that an aerodrome has a runway surface made of a specific construction material |
| case2_name_general | runwaySurfaceType | 877 | True |  |  |  |
| case2_name_general | school | 703 | True | HistoricalFigure | EducationalInstitution | indicates that a historical figure attended an educational institution |
| case2_name_general | selectedBy | 11 | True | Individual | GovernmentAgency | indicates that an individual is selected by a governmental agency |
| case2_name_general | selectedYear | 337 | True | HistoricalFigure | SelectionYear | indicates that a historical figure was selected in a specific year |
| case2_name_general | selectionYear | 11 | True | GovernmentAgency | Year | indicates that a governmental agency selects individuals in a specific year |
| case2_name_general | sells | 22 | True | PharmaceuticalCompany | PersonalCareProduct | indicates that a pharmaceutical company offers personal care products |
| case2_name_general | sequelTo | 307 | True | Book | Book | indicates that one book follows another in a series |
| case2_name_general | servedAs | 19 | True | DessertFood | Dessert | indicates that a dessert food item is specifically prepared as a sweet course at the end of a meal |
| case2_name_general | servedAt | 485 | True | SweetDish | DessertCourse | indicates that a sweet dish is served as part of a dessert course |
| case2_name_general | servedBy | 1155 | True | Aerodrome | Autodrome | represents the relationship where an aerodrome is managed by an autodrome |
| case2_name_general | servedFor | 569 | True | SweetDish | SweetMeal | indicates that a sweet dish is typically served as a dessert course |
| case2_name_general | serves | 56 | True | Aerodrome | Autodrome | indicates that an aerodrome facilitates the use of another facility |
| case2_name_general | servesAs | 569 | True | Nation | SweetDish | indicates that a nation is associated with a particular sweet dish |
| case2_name_general | serviceBranch | 154 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure served in a specific military branch |
| case2_name_general | singsIn | 716 | True | Musician | Band | represents the relationship where a musician is a member of a musical group |
| case2_name_general | southeastNeighbor | 501 | True | AdministrativeDivision | AdministrativeDivision | indicates that an administrative division is geographically located to the southeast of another |
| case2_name_general | southeastNeighbour | 165 | True | County | County | indicates that a county is geographically located southeast of another county |
| case2_name_general | southeastOf | 1116 | True | County | County | indicates that one county is geographically located to the southeast of another county |
| case2_name_general | southeast_of | 104 | True | County | County | indicates that one county is located southeast of another county |
| case2_name_general | southwestNeighbour | 165 | True | County | County | indicates that a county is geographically located southwest of another county |
| case2_name_general | sportsOffered | 522 | True | EducationalInstitution | RecreationalSport | indicates that an educational institution offers a recreational sport |
| case2_name_general | spouse | 28 | True | Politician | Individual | indicates that a politician is married to an individual |
| case2_name_general | staffCount | 871 | True | University | StaffCount | indicates that a university has a total number of staff members employed |
| case2_name_general | staffMembers | 66 | True | University | StaffMembers | indicates that a university has a specific number of individuals employed by the institution |
| case2_name_general | staffSize | 687 | True | University | StaffSize | indicates that a university has a specific number of staff members |
| case2_name_general | staffTotal | 768 | True | University | StaffTotal | indicates that a university has a total number of staff members |
| case2_name_general | starredIn | 472 | True | Actor | Broadcast | represents the relationship where an actor participates in a broadcast program |
| case2_name_general | starring | 91 | True | TV_series | Individual | indicates that a TV series features individual actors |
| case2_name_general | starringIn | 1133 | True | Actor | TVShow | indicates that an Actor is a key performer in a TVShow |
| case2_name_general | startDate | 997 | True | EducationalFacility | TemporalEntity | indicates that an educational facility was constructed on a specific date |
| case2_name_general | startDateConstruction | 112 | True | Structure | Year | indicates that construction on a building began on a specific year |
| case2_name_general | startedPerforming | 20 | True | Musician | Date | indicates that a musician began performing at a specific date |
| case2_name_general | state | 548 | True | AdministrativeDivision | AdministrativeDivision | represents the relationship where an administrative division belongs to a state |
| case2_name_general | stateOfDeath | 533 | True | Politician | State | indicates that a politician died in a specific state |
| case2_name_general | status | 146 | True | EducationalInstitution | EducationalStatus | indicates that an educational institution is recognized with a specific designation by a regulatory body |
| case2_name_general | studentBody_size | 379 | True | University | StudentBody_size | represents the relationship where a university has a total student body size |
| case2_name_general | studentCount_Doctoral | 871 | True | University | StudentCount_Doctoral | indicates that a university has a specific number of doctoral students enrolled |
| case2_name_general | studentCount_Postgraduate | 871 | True | University | StudentCount_Postgraduate | indicates that a university has a specific number of postgraduate students enrolled |
| case2_name_general | studentCount_Undergraduate | 871 | True | University | StudentCount_Undergraduate | indicates that a university has a specific number of undergraduate students enrolled |
| case2_name_general | studentType | 871 | True |  |  |  |
| case2_name_general | students | 336 | True | University | Students | indicates that a university has a total number of students enrolled |
| case2_name_general | studiedAt | 964 | True | Photographer | EducationalInstitution | indicates that a photographer pursued formal education at an applied arts school |
| case2_name_general | studiesAt | 36 | True | Person | EducationalInstitution | Indicates that a person studies at an educational institution. |
| case2_name_general | succeeded | 353 | True | Politician | Politician | indicates that one politician replaces another in a political leadership role |
| case2_name_general | succeededBy | 912 | True | Politician | Politician | represents the relationship where one politician is succeeded by another |
| case2_name_general | successor | 152 | True | Politician | Politician | represents the relationship where one politician succeeds another in a political role |
| case2_name_general | support | 610 | True | University | StudentPopulation | indicates that a university institution provides support services to a student body |
| case2_name_general | team | 42 | True | Player | Team | indicates that a player competes with a specific team |
| case2_name_general | teamLocation | 700 | True | Athlete | Stadium | indicates that an athletes team is based at a specific stadium |
| case2_name_general | technicalCampusAffiliation | 685 | True | EducationalInstitution | RegulatoryBody | indicates that an educational institution is affiliated with a regulatory body responsible for technical education |
| case2_name_general | timeZone | 73 | True | City | Timezone | indicates that a city operates within a specific time zone |
| case2_name_general | timezone | 61 | True | City | StandardTimezone | indicates that a city operates under a specific time zone |
| case2_name_general | toTheSouthEastOf | 107 | True | County | County | indicates that one county is located to the southeast of another county |
| case2_name_general | tookPartIn | 151 | True | Astronaut | SpaceMission | represents the relationship where an astronaut engages in a space-related activity |
| case2_name_general | totalArea | 802 | True | Country | Area | indicates that a country has a specific total area |
| case2_name_general | totalNumberOfStudents | 136 | True | University | TotalNumberOfStudents | indicates that a university has a comprehensive student body count |
| case2_name_general | totalStudents | 1107 | True | University | TotalNumberOfStudents | indicates that a university has a total count of all enrolled students |
| case2_name_general | type | 7 | True |  |  |  |
| case2_name_general | undergraduatePopulation | 702 | True | University | UndergraduatePopulation | represents the relationship where a university has a specific number of undergraduate students |
| case2_name_general | undergraduateStudentCount | 136 | True | University | UndergraduateStudentCount | indicates that a university has a specific count of undergraduate students |
| case2_name_general | undergraduateStudentPopulation | 932 | True | University | StudentPopulation | indicates that a university has a specific number of undergraduate students |
| case2_name_general | undergraduateStudents | 66 | True | University | UndergraduateStudents | indicates that a university has a specific number of students enrolled in undergraduate programs |
| case2_name_general | undergraduateTotal | 768 | True | University | UndergraduateTotal | indicates that a university has a specific number of undergraduate students |
| case2_name_general | undergraduates | 1127 | True | EducationalInstitution | Undergraduates | indicates that an educational institution has a count of students enrolled in undergraduate programs |
| case2_name_general | uses | 313 | True | DessertFood | Cheese | indicates that a dessert food item utilizes a specific ingredient |
| case2_name_general | utcOffset | 1 | True | City | UTCOffset | indicates that a city has a UTC offset |
| case2_name_general | wasAMemberOf | 1049 | True | Astronaut | SpaceMission | indicates that an astronaut participates in a specific spaceflight mission |
| case2_name_general | wasFoundedBy | 221 | True | BroadcastingCompany | FoundingEntity | indicates that a broadcasting company was founded by a specific founding entity |
| case2_name_general | wasInOfficeWhile | 728 | True | Individual | Presidency | indicates that an individual held a position during a specific presidency |
| case2_name_general | wasMarriedTo | 882 | True | Individual | Individual | indicates that an individual was married to another individual |
| case2_name_general | weight | 46 | True | Individual | Weight | indicates that an individuals weight is measured |
| case2_name_general | westNeighbor | 501 | True | AdministrativeDivision | AdministrativeDivision | indicates that an administrative division is geographically located to the west of another |
| case2_name_general | winLeague | 128 | True | SportsTeam | League | indicates that a sports team has won a league |
| case2_name_general | winLeagueTitle | 498 | True | SportsTeam | ProfessionalLeague | indicates that a sports team has won a league title |
| case2_name_general | wonChampionship | 293 | True | SportsTeam | League | indicates that a sports team achieved victory in a league organized by a governing body |
| case2_name_general | wonLeague | 1082 | True | SportsClub | League | indicates that a sports club has won a league championship |
| case2_name_general | wonLeagueChampionship | 189 | True | SportsTeam | Year | indicates that a sports team won a league championship in a specific year |
| case2_name_general | wrote | 351 | True | Author | Book | represents the relationship where an author creates a book |
| case2_name_general | year | 82 | True | League | Year | indicates that a league takes place in a specific year |
| case2_name_general | yearBegunCareer | 595 | True | Musician | Year | indicates that a musician began their musical career in a specific year |
| case2_name_general | yearErected | 247 | True | HistoricalMonument | Year | represents the relationship where a monument is associated with a specific year of erection |
| case2_name_general | yearInLeague | 128 | True | SportsTeam | Year | indicates that a sports team has been in a league for a specific year |
| case2_name_general | yearInPosition | 242 | True | HistoricalFigure | YearInPosition | indicates that a historical figure served in a leadership role for a specific year |
| case2_name_general | yearOfBirth | 909 | True | Individual | Year | indicates that an individual was born in a specific year |
| case2_name_general | yearOfConstruction | 836 | True | Monument | Year | indicates that a monument was constructed in a specific year |
| case2_name_general | yearOfDeath | 909 | True | Individual | Year | indicates that an individual died in a specific year |
| case2_name_general | yearOfGraduation | 557 | True | Historian | Year | indicates that a historian graduated from their educational institution in a specific year |
| case2_name_general | youthClub | 101 | True | Athlete | SportsTeam | indicates that an athlete is a member of the youth team of a sports club |
| case2_name_general | youthFootballClub | 1026 | True | Athlete | YouthFootballClub | indicates that an athlete was initially nurtured by a youth football club |
| case2_name_general | youthTeam | 219 | True | Athlete | FootballClub | indicates that an athlete began their career with a specific youth football club |
| case3_name_detail | CEO | 465 | True | Company | CEO | indicates that a company is led by a chief executive officer |
| case3_name_detail | aboveSeaLevel | 925 | True | City | AboveSeaLevel | indicates that a city is located above a certain sea level |
| case3_name_detail | absoluteMagnitude | 33 | True | Asteroid | AbsoluteMagnitude | indicates that an asteroid has a specific absolute magnitude |
| case3_name_detail | absolute_magnitude | 447 | True | CelestialBody | AbsoluteMagnitude | represents the relationship where an asteroid has a specific brightness measurement |
| case3_name_detail | actedIn | 111 | True | Actor | TelevisionSeries | indicates that an actor starred in a television series |
| case3_name_detail | actor | 1086 | True | TelevisionShow | Actor | indicates that a show features actors in its cast |
| case3_name_detail | address | 3 | True | ArchitecturalStructure | GeographicLocation | indicates that an architectural structure has a specific physical address |
| case3_name_detail | adjacentCounty | 185 | True | County | County | represents the relationship where one county is geographically adjacent to another county |
| case3_name_detail | affiliatedWith | 146 | True | EducationalInstitution | University | represents the relationship where an educational institution is associated with a university |
| case3_name_detail | affiliation | 17 | True | Institute | University | indicates that an educational institution is associated with a university for academic purposes |
| case3_name_detail | airedBananaman | 868 | True | BroadcastNetwork | TVSeries | represents the relationship where a broadcast network broadcasts a TV series |
| case3_name_detail | airedOn | 124 | True | TVSeries | BroadcastingCompany | indicates that a TV series is broadcasted by a specific broadcasting company |
| case3_name_detail | airedShowOn | 345 | True | BroadcastingCompany | EventDate | indicates that a broadcasting company aired a show on a specific date |
| case3_name_detail | altitudeAboveSeaLevel | 15 | True | Airport | Altitude | indicates that an airport is at a specific altitude above sea level |
| case3_name_detail | annualRevenue | 1157 | True | Company | AnnualRevenue | represents the total revenue generated by a company in a fiscal year |
| case3_name_detail | anthem | 225 | True | Monarchy | NationalAnthem | represents the relationship where a monarchy has a national anthem |
| case3_name_detail | apoapsis | 33 | True | Asteroid | Apoapsis | indicates that an asteroid has a specific apoapsis distance |
| case3_name_detail | architect | 3 | True | ArchitecturalStructure | Architect | indicates that an architectural structure is designed by a professional architect |
| case3_name_detail | architected | 946 | True | Professional | Structure | indicates that an architect designed a specific building |
| case3_name_detail | area | 200 | True | Country | Area | represents the relationship where a countrys geographical extent is quantified |
| case3_name_detail | areaCode | 74 | True | Place | AreaCode | represents the relationship where a place is uniquely identified by a numeric area code |
| case3_name_detail | assembledIn | 994 | True | Automobile | City | indicates that an automobile is manufactured in a specific city |
| case3_name_detail | assemblyLineLocation | 39 | True | Vehicle | City | indicates that a vehicle was produced on an assembly line located within a city |
| case3_name_detail | assemblyLocation | 520 | True | Automobile | City | indicates that an automobile is assembled in a specific city |
| case3_name_detail | associatedBand | 108 | True | Musician | Band | indicates that a musician is associated with a musical group |
| case3_name_detail | associatedWith | 400 | True | Musician | Musician | indicates that a musician collaborates with another artist in musical projects |
| case3_name_detail | attendedSchool | 63 | True | Student | EducationalInstitution | represents the relationship where a student is enrolled in an educational institution |
| case3_name_detail | author | 72 | True | Book | Author | indicates that a book is authored by an individual |
| case3_name_detail | award | 154 | True | HistoricalFigure | MilitaryAward | indicates that a historical figure received a specific military award |
| case3_name_detail | awarded | 599 | True | HistoricalFigure | Medal | represents the relationship where a historical figure receives a distinguished service medal |
| case3_name_detail | awardedBy | 349 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure received a military award from a branch of the armed forces |
| case3_name_detail | awardedTechnicalCampusStatusTo | 131 | True | GovernmentAgency | EducationalInstitution | represents the relationship where a government agency grants a technical campus status to an educational institution |
| case3_name_detail | awardedTo | 154 | True | MilitaryBranch | HistoricalFigure | indicates that a military branch awards a specific historical figure a medal |
| case3_name_detail | awardingBody | 615 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure is awarded by a specific military branch |
| case3_name_detail | beganCareerIn | 893 | True | Musician | Date | indicates that a musician starts their professional career at a specific date |
| case3_name_detail | beganMusicalCareer | 400 | True | Musician | Year | represents the relationship where a musician starts their professional music career |
| case3_name_detail | beganPerforming | 376 | True | Musician | Date | indicates that a musician starts performing at a specific point in time |
| case3_name_detail | birthDate | 13 | True | MilitaryPerson | Date | indicates that a military person was born on a specific date |
| case3_name_detail | birthPlace | 13 | True | MilitaryPerson | City | indicates that a military person is born in a specific city |
| case3_name_detail | birthYear | 34 | True | HistoricalFigure | Year | indicates that a historical figure was born in a specific year |
| case3_name_detail | bodyStyle | 399 | True | Automobile | BodyStyle | represents the relationship where an automobile has a specific body style |
| case3_name_detail | borderingCounty | 906 | True | County | County | indicates that a county shares borders with other counties |
| case3_name_detail | born | 364 | True | Astronaut | BirthDate | indicates that an astronaut was born on a specific date |
| case3_name_detail | bornIn | 4 | True | Individual | City | indicates that an individual is born in a specific city |
| case3_name_detail | bornOn | 30 | True | Athlete | BirthDate | indicates that an athlete was born on a specific date |
| case3_name_detail | bornWithin | 357 | True | Individual | Monarchy | indicates that an individual was born within a monarchy |
| case3_name_detail | born_on | 805 | True | Astronaut | BirthDate | indicates that an astronaut was born on a specific date |
| case3_name_detail | broadcastedBy | 6 | True | TVShow | BroadcastingCompany | indicates that a TV show is broadcast by a specific broadcasting company |
| case3_name_detail | broughtUpBy | 250 | True | MediaCompany | AnimatedCharacter | represents the relationship where a media company is associated with a specific animated character |
| case3_name_detail | buildStartDate | 965 | True | EducationalBuilding | TemporalValue | indicates that a building was constructed on a specific date |
| case3_name_detail | builder | 105 | True | Locomotive | Company | represents the relationship where a locomotive is produced by a manufacturing company |
| case3_name_detail | builtBy | 757 | True | EducationalBuilding | Architect | represents the relationship where an educational building is designed by an architect |
| case3_name_detail | builtIn | 7 | True | HistoricalStructure | TimePeriod | indicates that a historical structure is constructed in a specific year |
| case3_name_detail | builtOn | 278 | True | EducationalBuilding | ConstructionDate | indicates that an educational building was constructed on a specific date |
| case3_name_detail | campusLocation | 410 | True | University | Road | indicates that a university is situated on a specific road within its campus |
| case3_name_detail | campusStatus | 974 | True | EducationalInstitution | CampusStatus | indicates that an educational institution has been granted a specific status by a governing body |
| case3_name_detail | campus_location | 563 | True | EducationalInstitution | Address | indicates that an educational institution has a specific campus location |
| case3_name_detail | categorization | 501 | True | HistoricalStructure | HistoricResource | indicates that a historical structure is recognized as a resource contributing to the significance of a district |
| case3_name_detail | category | 104 | True |  |  |  |
| case3_name_detail | ceremonialCounty | 830 | True | Town | CeremonialCounty | represents the relationship where a town is part of a ceremonial county |
| case3_name_detail | championOf | 659 | True | SportsTeam | League | represents the relationship where a sports team is the champion of a league |
| case3_name_detail | champions | 16 | True | SportsTeam | League | indicates that a sports team is the champion of a league |
| case3_name_detail | championship | 920 | True | SportsClub | League | indicates that a sports club has won a specific league championship |
| case3_name_detail | championships | 629 | True | SportsTeam | Number | indicates that a sports team has won a specific number of championships |
| case3_name_detail | channel | 384 | True | TVSeries | BroadcastingCompany | indicates that a TV series is broadcasted on a specific television channel operated by a broadcasting company |
| case3_name_detail | character | 688 | True | Actor | TelevisionSeries | indicates that an actor portrays a character in a television series |
| case3_name_detail | citizenship | 326 | True | Politician | Citizen | indicates that a politician holds a specific citizenship status |
| case3_name_detail | city | 418 | True | EducationalInstitution | City | indicates that an educational institution is located in a specific city |
| case3_name_detail | cityManagerTitle | 73 | True | City | CityManager | indicates that a city is led by a city manager |
| case3_name_detail | coach | 295 | True | Team | Coach | represents the relationship where a coach leads a sports team |
| case3_name_detail | competedIn | 284 | True | SportsTeam | Season | represents the relationship where a sports team participated in a specific season |
| case3_name_detail | completedOn | 190 | True | ArchitecturalStructure | CompletionDate | indicates that an architectural structure is finished on a specific completion date |
| case3_name_detail | completionDate | 112 | True | Structure | Year | indicates that a building was completed on a specific year |
| case3_name_detail | constructedBy | 47 | True | Structure | Architect | represents the relationship where a structure is designed by an architect |
| case3_name_detail | constructionPeriod | 47 | True | Structure | Period | indicates that a structure was built within a specific time frame |
| case3_name_detail | constructionStart | 361 | True | Facility | Temporal | indicates that a facilitys construction began on a specific date |
| case3_name_detail | constructionStartDate | 1121 | True | EducationalBuilding | ConstructionStartDate | indicates that an educational building has a specific start date for construction |
| case3_name_detail | constructionStartedOn | 887 | True | Structure | Temporal | indicates that the construction of a constructed facility began on a specific date |
| case3_name_detail | contains | 58 | True | SweetDessert | CondensedMilk | indicates that a dessert includes a specific dairy product |
| case3_name_detail | containsAdministrativeTerritory | 431 | True | AdministrativeTerritory | AdministrativeTerritory | Indicates that an administrative territory contains another administrative territory. |
| case3_name_detail | containsIngredient | 986 | True | Dish | Nutrition | indicates that a dish includes granola, shredded coconut, and raisins as nutritional ingredients |
| case3_name_detail | containsSettlement |  | False | AdministrativeTerritory | Settlement | Indicates that an administrative territory contains a settlement such as a city or town. |
| case3_name_detail | containsTeam | 284 | True | League | SportsTeam | represents the relationship where a league includes multiple sports teams |
| case3_name_detail | corporateForm | 29 | True | Company | LegalForm | represents the relationship where a company has a specific legal form |
| case3_name_detail | cosparId | 416 | True | SpaceMission | CosparId | represents the relationship where a space mission is uniquely identified by a COSPAR ID |
| case3_name_detail | country | 3 | True | EducationalInstitution | Country | indicates that an educational institution is located in a specific country |
| case3_name_detail | countryOfBirth | 356 | True | HistoricalFigure | Country | represents the relationship where a historical figure is born in a specific country |
| case3_name_detail | countryOfCitizenship | 311 | True | Politician | Nation | indicates that a politician holds citizenship in a sovereign state |
| case3_name_detail | countryOfDeath | 689 | True | GeopoliticalEntity | GeopoliticalEntity | indicates that a sovereign state is the place where an individual died |
| case3_name_detail | countryOfOrigin | 674 | True | AutomobileCompany | Nation | represents the relationship where an automobile company is founded in a particular nation |
| case3_name_detail | countryOrigin | 369 | True | Sweet | Nation | indicates that a sweet dessert originates from a specific nation |
| case3_name_detail | county | 7 | True | HistoricalStructure | County | indicates that a historical structure is situated within a county |
| case3_name_detail | created | 562 | True | Creator | AnimatedCharacter | indicates that a creator produces an animated character |
| case3_name_detail | creator | 6 | True | TVShow | Creator | represents the relationship where a TV show is created by a specific creator |
| case3_name_detail | crew | 703 | True | HistoricalFigure | SpaceMission | indicates that a historical figure was a member of a specific space mission |
| case3_name_detail | crewMember | 332 | True | SpaceMission | Citizen | indicates that a space mission includes a citizen as a crew member |
| case3_name_detail | crewMemberOf | 827 | True | Astronaut | SpaceMission | represents the relationship where an astronaut serves as a crew member on a space mission |
| case3_name_detail | currency | 24 | True | GeopoliticalEntity | MonetaryUnit | indicates that a country uses a specific currency for transactions |
| case3_name_detail | currentAssemblyLocation | 697 | True | Automobile | City | indicates that an automobile is currently assembled in a specific city |
| case3_name_detail | currentClub | 30 | True | Athlete | FootballClub | indicates that an athlete is currently affiliated with a football club |
| case3_name_detail | currentLeader | 699 | True | Nation | Politician | represents the relationship where a nation is led by a political leader |
| case3_name_detail | currentLocation | 187 | True | Company | Country | indicates that a company is headquartered in a specific country |
| case3_name_detail | currentPosition | 156 | True | Politician | PoliticalOffice | represents the relationship where a politician holds a current political office position |
| case3_name_detail | currentSenator | 476 | True | State | Politician | represents the relationship where a state is governed by a current senator |
| case3_name_detail | currentTeam | 42 | True | Player | Team | represents the relationship where a player is currently associated with a specific team |
| case3_name_detail | currentTenant | 730 | True | EducationalBuilding | EducationalInstitution | indicates that an educational building houses an educational institution |
| case3_name_detail | currentTenants | 3 | True | ArchitecturalStructure | EducationalInstitution | indicates that an architectural structure is currently occupied by an educational institution |
| case3_name_detail | currentlyPlaysFor | 95 | True | Athlete | SportsTeam | indicates that an athlete is currently affiliated with a sports team |
| case3_name_detail | cylinderCount | 878 | True | Locomotive | CylinderCount | indicates that a locomotive has a specific number of cylinders |
| case3_name_detail | dateOfBirth | 25 | True | Individual | BirthDate | indicates that an individual has a specific birth date |
| case3_name_detail | dateOfDeath | 173 | True | Individual | DeathDate | indicates that an individual died on a specific date |
| case3_name_detail | dateOfRetirement | 154 | True | HistoricalFigure | RetirementDate | indicates that a historical figure retired on a specific date |
| case3_name_detail | dateOfRole | 633 | True | HistoricalFigure | HistoricalYear | indicates that a historical figure held a role in a specific year |
| case3_name_detail | deathCause | 640 | True | Individual | Death | indicates that an individuals death is caused by a natural or medical condition |
| case3_name_detail | deathDate | 93 | True | Individual | DeathDate | indicates that an individual has a specific death date |
| case3_name_detail | deathPlace | 28 | True | Politician | Nation | indicates that a politician died in a specific nation |
| case3_name_detail | debutTeam | 425 | True | Player | Team | indicates that a player made their initial appearance for a specific team |
| case3_name_detail | degree | 477 | True | EducationalInstitution | Degree | indicates that an educational institution awarded a specific degree |
| case3_name_detail | designatedAs | 643 | True | EducationalInstitution | CampusDesignation | represents the relationship where an educational institution is given a specific designation or classification |
| case3_name_detail | designatedTechnicalCampusStatusTo | 143 | True | Council | Institute | indicates that a council formally recognizes a technical education institution as a campus |
| case3_name_detail | designed | 887 | True | Professional | Structure | indicates that a professional architect created the design for a constructed facility |
| case3_name_detail | diedDateTime | 991 | True | Individual | DateTime | indicates that an individual died on a specific date and time |
| case3_name_detail | diedIn | 4 | True | Individual | Country | indicates that an individual dies in a specific country |
| case3_name_detail | directedBy | 643 | True | EducationalInstitution | EducationalLeader | indicates that an educational institution is led by a person in charge of academic affairs |
| case3_name_detail | direction | 365 | True | AdministrativeDivision | GeographicalDirection | indicates that a territorial division is geographically positioned relative to another |
| case3_name_detail | director | 131 | True | EducationalInstitution | Educator | represents the relationship where an educational institution is led by an educator |
| case3_name_detail | discovered | 182 | True | Astronomer | AstronomicalBody | indicates that an astronomer identifies a celestial body |
| case3_name_detail | discoveredBy | 33 | True | Asteroid | Astronomer | indicates that an asteroid is identified by an astronomer |
| case3_name_detail | discoveryDate | 33 | True | Asteroid | Date | indicates that an asteroids discovery is recorded with a specific date |
| case3_name_detail | doctoralStudents | 66 | True | University | DoctoralStudents | indicates that a university has a specific number of students enrolled in doctoral programs |
| case3_name_detail | draftPick | 518 | True | Athlete | DraftPick | indicates that an athlete is selected as a draft pick |
| case3_name_detail | draftPickNumber | 1057 | True | Athlete | DraftPickNumber | indicates that an athlete is assigned a draft pick number |
| case3_name_detail | earnings | 85 | True | Company | Earnings | indicates that a company generates financial income over a year |
| case3_name_detail | eat | 790 | True | Dessert | Type | indicates that a dessert is consumed as a type of food |
| case3_name_detail | educate | 537 | True | University | StudentCount | indicates that a university enrolls a specific number of students |
| case3_name_detail | educatedAt | 707 | True | FootballClub | Athlete | indicates that a football club has an athlete as a former member |
| case3_name_detail | education | 53 | True | HistoricalFigure | Degree | indicates that a historical figure has earned a formal academic degree |
| case3_name_detail | elevationAboveSeaLevel | 41 | True | Airport | ElevationAboveSeaLevel | indicates that an airport has a specific elevation above sea level measurement |
| case3_name_detail | endedManufacturingOf | 325 | True | Automaker | AutomobileModel | indicates that an automaker ceases production of a specific vehicle model |
| case3_name_detail | engine | 350 | True | Locomotive | Engine | indicates that a locomotive is equipped with a particular type of engine |
| case3_name_detail | engineConfiguration | 749 | True | Locomotive | EngineConfiguration | indicates that a locomotive employs a particular engine configuration |
| case3_name_detail | enrollment | 70 | True | University | StudentCount | represents the relationship where a university has a specific number of students enrolled |
| case3_name_detail | epoch | 64 | True | Asteroid | Time | represents the relationship where an asteroid reaches a specific epoch in its orbit |
| case3_name_detail | epochDate | 958 | True | CelestialBody | Date | indicates that a celestial body has a specific reference date |
| case3_name_detail | erectedIn | 638 | True | Monument | State | indicates that a monument is erected in a specific state |
| case3_name_detail | established | 48 | True | HistoricalMonument | TimePeriod | indicates that a historical monument is founded in a specific year |
| case3_name_detail | establishedIn | 146 | True | EducationalInstitution | Year | indicates that an educational institution was founded in a specific year |
| case3_name_detail | establishmentYear | 138 | True | Monument | Year | indicates that a monument was established in a specific year |
| case3_name_detail | ethnicGroup | 4 | True | Country | Group | represents the relationship where a country has a specific ethnic group |
| case3_name_detail | extinctionDate | 558 | True | AutomobileBrand | Year | represents the relationship where an automobile brand ceased operations on a specific year |
| case3_name_detail | firstAired | 6 | True | TVShow | EventDate | indicates that a TV show marks its premiere on a specific date |
| case3_name_detail | firstAiredBy | 698 | True | TelevisionShow | BroadcastingCompany | indicates that a television show is broadcasted by a specific broadcasting company |
| case3_name_detail | firstAiredOn | 672 | True | TVSeries | EventDate | indicates that a TVSeries has a specific event date of its premiere |
| case3_name_detail | firstAppearance | 260 | True | Film | AnimatedCharacter | represents the relationship where a film features its initial appearance of an animated character |
| case3_name_detail | firstAppearedAsFilmCharacterIn | 779 | True | FilmCharacter | Film | represents the relationship where a characters first appearance in a film is specified |
| case3_name_detail | firstAppearedIn | 824 | True | AnimatedCharacter | Film | represents the relationship where an animated characters debut is in a movie |
| case3_name_detail | firstBroadcast | 250 | True | AnimatedCharacter | EventDate | indicates that an animated character had its first broadcast on a specific date |
| case3_name_detail | firstProducedIn | 199 | True | Automobile | Year | indicates that an automobile was first manufactured in a specific year |
| case3_name_detail | firstProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was first manufactured in a specific year |
| case3_name_detail | followedBy | 241 | True | Book | Book | indicates that one book series continues another in a narrative sequence |
| case3_name_detail | follows | 585 | True | Book | Book | indicates that one book comes after another in a series |
| case3_name_detail | foodServedAsDessert | 811 | True | Nation | Dessert | indicates that a nation serves a specific dessert as a dessert |
| case3_name_detail | formerTeam | 414 | True | Athlete | SportsTeam | indicates that an athlete has previously been associated with a specific sports team |
| case3_name_detail | formerlyPlayedFor | 782 | True | Athlete | SportsTeam | indicates that an athlete previously played for a sports team |
| case3_name_detail | formerlyPlayedWith | 318 | True | Athlete | SportsTeam | indicates that an athlete previously played for a sports team |
| case3_name_detail | foundIn | 19 | True | DessertFood | Country | represents the relationship where a dessert food item is located within a specific country |
| case3_name_detail | founded | 114 | True | Company | Date | indicates that a company was established on a specific date |
| case3_name_detail | foundedBy | 120 | True | Company | Founder | represents the relationship where a company is initiated by a person |
| case3_name_detail | foundedIn | 1161 | True | Company | City | indicates that a company was established in a specific city |
| case3_name_detail | founder | 62 | True | Company | Founder | represents the relationship where a company is initiated and managed by a founder |
| case3_name_detail | founding | 691 | True | City | HistoricalFigure | represents the relationship where a city is founded by a historical figure |
| case3_name_detail | foundingDate | 22 | True | PharmaceuticalCompany | FoundingDate | indicates that a pharmaceutical company was established on a specific founding date |
| case3_name_detail | foundingEntity | 221 | True | BroadcastingCompany | FoundingEntity | represents the relationship where a broadcasting company is established by a founding entity |
| case3_name_detail | foundingFather | 1014 | True | BroadcastingCompany | FoundingFather | represents the relationship where a broadcasting company was established by a founding father |
| case3_name_detail | foundingPerson | 831 | True | Company | Founder | indicates that a company was founded by a specific person |
| case3_name_detail | foundingPlace | 114 | True | Company | City | indicates that a company was founded in a specific city |
| case3_name_detail | foundingYear | 1024 | True | Aerodrome | Year | indicates that an aerodrome was founded in a specific year |
| case3_name_detail | from | 936 | True | Musician | Thing | indicates that a musician is associated with a specific geographic entity |
| case3_name_detail | fullAddress | 392 | True | Institute | Address | indicates that an institute has a specific full physical address |
| case3_name_detail | fullName | 203 | True | State | Name | indicates that a state has a formal name |
| case3_name_detail | full_name | 246 | True | SportsTeam | SportsTeam | indicates that a sports team has a formal name |
| case3_name_detail | gaveStatusBy | 857 | True | EducationalInstitution | EducationalAuthority | indicates that an educational institution is granted a status by an educational authority |
| case3_name_detail | genre | 91 | True | TV_series | Series | indicates that a TV series belongs to a specific series category |
| case3_name_detail | governingBody | 748 | True | City | Position | indicates that a city is governed by a specific leadership position |
| case3_name_detail | governmentForm | 1036 | True | StateFormOfGovernment | UnitaryState | indicates that a state form of government is characterized by a centralized system of governance |
| case3_name_detail | governmentType | 1 | True |  |  |  |
| case3_name_detail | governor | 925 | True | City | GovernmentBody | indicates that a city is governed by a government body |
| case3_name_detail | graduatedFrom | 512 | True | HistoricalFigure | EducationalInstitution | indicates that a historical figure received a degree from an educational institution |
| case3_name_detail | graduatedIn | 703 | True | HistoricalFigure | Year | indicates that a historical figure graduated in a specific year |
| case3_name_detail | graduationYear | 242 | True | HistoricalFigure | GraduationYear | indicates that a historical figure completed an educational program in a specific year |
| case3_name_detail | ground | 16 | True | Stadium | SportsTeam | indicates that a stadium hosts a sports team |
| case3_name_detail | hadCampusIn | 492 | True | University | City | indicates that a university had its campus within a specific city |
| case3_name_detail | has | 48 | True | AdministrativeDivision | AdministrativeDivision | indicates that a territorial division contains another territorial division |
| case3_name_detail | hasBird | 282 | True | State | Species | represents the relationship where a state is associated with a specific bird species |
| case3_name_detail | hasDessert | 791 | True | City | SweetDish | indicates that a city has a specific dessert dish |
| case3_name_detail | hasFood | 945 | True | Nation | Dessert | indicates that a nation includes a specific type of food in its culinary offerings |
| case3_name_detail | hasIngredient | 892 | True | Dessert | Ingredient | indicates that a dessert contains a specific ingredient |
| case3_name_detail | hasItem | 171 | True | UrbanCenter | SweetFood | represents the relationship where an urban center has another specific type of sweet food item |
| case3_name_detail | hasMember | 376 | True | Band | Musician | represents the relationship where a band includes a musician as one of its members |
| case3_name_detail | hasNativeBird | 505 | True | State | Bird | represents the relationship where a state is home to a specific native bird species |
| case3_name_detail | hasOfficial | 493 | True | State | Official | represents the relationship where a state appoints an official to lead its administration |
| case3_name_detail | hasPart | 727 | True | GeographicArea | GeographicArea | represents the relationship where one geographic area contains another |
| case3_name_detail | hasPopulationDensity | 669 | True | Country | PopulationDensity | represents the relationship where a country has a specific population density |
| case3_name_detail | hasSenator | 789 | True | State | Politician | represents the relationship where a state has a senator |
| case3_name_detail | hasSubsidiary | 85 | True | Company | Subsidiary | represents the relationship where a company maintains a subsidiary organization |
| case3_name_detail | hasTeam | 524 | True | ProfessionalLeague | SportsClub | represents the relationship where a professional league has a team belonging to a sports club |
| case3_name_detail | hasUndergraduateStudents | 462 | True | University | UndergraduateStudents | indicates that a university enrolls a specific number of undergraduate students |
| case3_name_detail | hasVariation | 985 | True | Dessert | Dessert | indicates that a dessert has a variation of another dessert |
| case3_name_detail | headquarteredIn | 386 | True | University | City | indicates that a university is geographically located within a specific city |
| case3_name_detail | headquarters | 111 | True | TelevisionNetwork | Headquarters | indicates that a television network has its administrative center in a specific building |
| case3_name_detail | headquartersLocation | 99 | True | AirlineCompany | City | indicates that an airline company has its headquarters in a city |
| case3_name_detail | height | 90 | True | Athlete | Height | indicates that an athlete has a specific height measurement |
| case3_name_detail | heldOfficeWhile | 862 | True | Politician | Politician | indicates that a politician held office during the tenure of another politician |
| case3_name_detail | homeGround | 88 | True | SportsTeam | Stadium | indicates that a sports team has a designated home ground venue |
| case3_name_detail | icaoIdentifier | 355 | True | Aerodrome | ICAOIdentifier | indicates that an aerodrome is assigned a unique ICAO identifier |
| case3_name_detail | icaoLocationIdentifier | 14 | True | Aerodrome | ICAOIdentifier | represents the relationship where an aerodrome is assigned a unique ICAO identifier |
| case3_name_detail | inOfficeWith | 344 | True | Politician | Politician | indicates that two politicians held office simultaneously |
| case3_name_detail | industry | 187 | True | Company | BuildingMaterials | represents the relationship where a company operates within a specific industry category |
| case3_name_detail | ingredient | 147 | True | MexicanDessert | DairyProduct | indicates that a Mexican dessert contains a dairy-based ingredient |
| case3_name_detail | ingredients | 24 | True | DessertFood | FoodIngredients | indicates that a dessert food is composed of specific ingredients |
| case3_name_detail | inhabit | 790 | True | Nation | Country | represents the relationship where a nation is inhabited by a specific country |
| case3_name_detail | inhabitant | 24 | True | GeopoliticalEntity | HumanPopulation | represents the relationship where a country is populated by its inhabitants |
| case3_name_detail | inhabitants | 67 | True | Country | Population | indicates that a country is inhabited by a population |
| case3_name_detail | inhabitedBy | 421 | True | Nation | Population | indicates that a nation is inhabited by a specific demographic group of people |
| case3_name_detail | inhabits | 853 | True | State | Bird | represents the relationship where a state is home to a specific bird species |
| case3_name_detail | is | 826 | True | Thing | Thing | represents the relationship where an entity belongs to a specific category |
| case3_name_detail | isA | 19 | True |  |  |  |
| case3_name_detail | isAffiliatedTo | 133 | True |  |  |  |
| case3_name_detail | isAffiliatedWith | 198 | True |  |  |  |
| case3_name_detail | isAnEthnicGroup | 1034 | True |  |  |  |
| case3_name_detail | isAssociatedWith | 131 | True |  |  |  |
| case3_name_detail | isBasedAt | 345 | True | BroadcastingCompany | Building | indicates that a broadcasting company operates from a physical workplace |
| case3_name_detail | isBasedIn | 51 | True | Airport | City | indicates that an airport is geographically located within a city |
| case3_name_detail | isCapitalOf | 669 | True | Country | Country | represents the relationship where a country is the capital of itself |
| case3_name_detail | isCategorizedAs | 48 | True | HistoricalMonument | HistoricProperty | indicates that a historical monument is classified as a significant property |
| case3_name_detail | isCategoryOf | 727 | True |  |  |  |
| case3_name_detail | isChampion | 82 | True | SportsClub | BooleanValue | indicates that a sports club is the champion of a league |
| case3_name_detail | isChampionOf | 284 | True | SportsTeam | League | indicates that a sports team won a championship in a league competition |
| case3_name_detail | isChiefOf | 866 | True | HistoricalFigure | AerospaceAgency | indicates that a historical figure leads an aerospace agency |
| case3_name_detail | isContributing_Property | 873 | True | HistoricalMonument | TrueValue | represents the relationship where a historical monument is considered significant or contributing to a site |
| case3_name_detail | isDessert | 791 | True | SweetDish | LogicalValue | represents the relationship where a dessert dish is classified as a dessert |
| case3_name_detail | isEthnicGroup | 437 | True | Community | Nation | indicates that an ethnic group belongs to a sovereign nation |
| case3_name_detail | isEthnicGroupIn | 1164 | True | Ethnicity | Location | a relation between Ethnicity and Location |
| case3_name_detail | isFoundationPlace | 499 | True | FoundationPlace | FoundationPlace | indicates that a FoundationPlace serves as the origin or basis of another FoundationPlace |
| case3_name_detail | isFrom | 725 | True | Individual | Thing | indicates that an individual is from a specific entity |
| case3_name_detail | isHomeTo | 466 | True | EducationalBuilding | EducationalInstitution | indicates that an educational building houses an educational institution |
| case3_name_detail | isLeaderIn | 1160 | True | Politician | Nation | indicates that a politician leads a nation |
| case3_name_detail | isLeaderOf | 303 | True | Politician | Thing | indicates that a politician holds leadership over a specific entity |
| case3_name_detail | isLeagueChampion | 189 | True | SportsTeam | ChampionStatus | indicates that a sports team is the current champion of a league |
| case3_name_detail | isLocatedIn | 48 | True | HistoricalMonument | Municipality | indicates that a historical monument is located within a populated place |
| case3_name_detail | isLocationOf | 969 | True | Country | Population | represents the relationship where a country is the location of its population |
| case3_name_detail | isManagedBy | 367 | True | City | GovernmentPosition | indicates that a city is managed by a specific government position |
| case3_name_detail | isMemberOf | 50 | True | Musician | Band | represents the relationship where a musician is part of a musical group |
| case3_name_detail | isNationalityOf | 669 | True | Country | Individual | indicates that a country is the nationality of an individual |
| case3_name_detail | isNear | 744 | True | HistoricalMonument | County | indicates that a historical monument is located near another county |
| case3_name_detail | isPartOf | 1 | True | City | State | indicates that a city is administratively part of a state |
| case3_name_detail | isServedAs | 305 | True | FoodItem | MealComponent | represents the relationship where a food item is part of a meal course |
| case3_name_detail | isServedBy | 354 | True | Autodrome | Aerodrome | indicates that an autodrome is served by another location |
| case3_name_detail | isStarOf | 562 | True | Actor | AnimatedCharacter | indicates that an actor stars in an animated character |
| case3_name_detail | isType | 1077 | True |  |  |  |
| case3_name_detail | isWestOf | 836 | True | City | County | indicates that a city is located west of a county |
| case3_name_detail | jobTitle | 771 | True | MilitaryPerson | MilitaryRole | indicates that a military person holds a specific combat leadership role |
| case3_name_detail | keyPerson | 461 | True | PharmaceuticalCompany | Executive | represents the relationship where a pharmaceutical company is led by a high-ranking executive |
| case3_name_detail | keyPersonAt | 1048 | True | KeyPerson | Company | indicates that a key person holds a significant role within a company organization |
| case3_name_detail | keyPersonFor | 609 | True | KeyPerson | Company | indicates that a key person oversees a company |
| case3_name_detail | language | 340 | True | Nation | ModernLanguage | represents the relationship where a nation employs a modern form of a language |
| case3_name_detail | lastAired | 366 | True | TVSeries | EventDate | indicates that a TV series concludes on a specific event date |
| case3_name_detail | lastAiredOn | 167 | True | Program | Date | indicates that a program was last aired on a specific date |
| case3_name_detail | lastProducedIn | 199 | True | Automobile | Year | indicates that an automobile was last manufactured in a specific year |
| case3_name_detail | lastProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was last manufactured in a specific year |
| case3_name_detail | leader | 196 | True | City | Politician | represents the relationship where a city is governed by a political leader |
| case3_name_detail | leaderName | 251 | True | City | Leader | represents the relationship where a city is led by a specific person |
| case3_name_detail | leaderTitle | 1 | True | City | LeaderTitle | indicates that a city has a leadership role title |
| case3_name_detail | leadershipTitle | 280 | True | Country | LeadershipRole | indicates that a country has a specific title for its leadership role |
| case3_name_detail | league | 16 | True | SportsTeam | League | indicates that a sports team competes in a specific league |
| case3_name_detail | leagueTitle | 975 | True | SportsTeam | League | indicates that a sports team competes in a specific league title |
| case3_name_detail | length | 2 | True | Locomotive | Length | represents the relationship where a locomotives physical dimension is defined |
| case3_name_detail | locatedAboveSeaLevel | 83 | True | Airport | Altitude | indicates that an airport is at a specific elevation above sea level |
| case3_name_detail | locatedAt | 643 | True | EducationalInstitution | Address | represents the specific address or location of an educational institution |
| case3_name_detail | locatedIn | 614 | True | Dessert | Location | indicates that a dessert is served in a specific geographical location |
| case3_name_detail | locatedInAdministrativeTerritory | 15 | True | Location | AdministrativeTerritory | Indicates that a location is located within a specific administrative territorial entity. |
| case3_name_detail | locatedInCountry | 110 | True | Location | Country | Indicates that a location is located in a country. |
| case3_name_detail | location | 0 | True | Company | City | represents the relationship where a companys physical presence is located within a city |
| case3_name_detail | locationCity | 872 | True | BroadcastingCompany | City | indicates that a broadcasting company is headquartered in a specific city |
| case3_name_detail | locationElevation | 56 | True | Aerodrome | Elevation | indicates that an aerodrome has a specific elevation above sea level |
| case3_name_detail | locationInTimezone | 852 | True | City | Zone | indicates that a city is located in a specific time zone |
| case3_name_detail | locationOf | 498 | True | Stadium | SportsTeam | indicates that a stadium is the home ground of a sports team |
| case3_name_detail | locationOfBroadcast | 167 | True | Program | Building | indicates that a program is broadcast from a specific building |
| case3_name_detail | locationOfDeath | 173 | True | Country | Country | indicates that a country is the location of an individual's death |
| case3_name_detail | locationOfFounding | 808 | True | Company | City | indicates that a company was founded in a specific city location |
| case3_name_detail | locationOfManufacture | 580 | True | Automobile | City | indicates that an automobile is manufactured in a specific city |
| case3_name_detail | locationOfOccurrence | 449 | True | Ingredient | Country | indicates that an ingredient is found within a specific country |
| case3_name_detail | locationOfProduction | 199 | True | Automobile | City | indicates that an automobile was produced in a specific city |
| case3_name_detail | locationRelation | 78 | True | County | SpatialRelation | represents the relationship where a county is situated relative to another county in a north-south direction |
| case3_name_detail | longName | 174 | True | Nation | OfficialName | represents the relationship where a nations long name corresponds to its official name |
| case3_name_detail | madeAutomobile | 507 | True | AutomobileCompany | Automobile | represents the relationship where an automobile company creates a vehicle product |
| case3_name_detail | magnitude | 739 | True | Asteroid | Magnitude | indicates that an asteroid has a numerical measure of its brightness |
| case3_name_detail | mainDishType | 421 | True |  |  |  |
| case3_name_detail | mainIngredient | 329 | True | Dessert | DairyProduct | indicates that a dessert contains raisins |
| case3_name_detail | mainProduct | 27 | True | Company | Software | represents the relationship where a company specializes in creating software products |
| case3_name_detail | makes | 22 | True | PharmaceuticalCompany | Medicine | indicates that a pharmaceutical company produces medical products |
| case3_name_detail | makesProduct | 627 | True | Company | Software | indicates that a company produces software products |
| case3_name_detail | manager | 5 | True | SportsTeam | Manager | indicates that a sports team is led by a manager |
| case3_name_detail | managerOfCurrentTeam | 572 | True | Athlete | Manager | indicates that an athlete has a manager for their current team |
| case3_name_detail | managerTitle | 29 | True | Company | ManagerTitle | indicates that a company is managed by a specific title |
| case3_name_detail | manages | 192 | True | Athlete | Coach | represents the relationship where an athlete oversees a coaching role |
| case3_name_detail | manufacturer | 281 | True | Locomotive | Manufacturer | indicates that a locomotive is produced by a specific manufacturer |
| case3_name_detail | marriage | 640 | True | Individual | Individual | indicates that two individuals are legally or socially united in marriage |
| case3_name_detail | member | 343 | True | Band | Musician | indicates that a band has a musician as one of its members |
| case3_name_detail | memberOf | 30 | True | Athlete | YouthTeam | indicates that an athlete is a member of a youth sports team |
| case3_name_detail | mission | 25 | True | Individual | SpaceMission | indicates that an individual participates in a spaceflight mission |
| case3_name_detail | monumentCategory | 955 | True |  |  |  |
| case3_name_detail | movedTo | 1161 | True | Company | Country | indicates that a company relocated to a specific country |
| case3_name_detail | municipality | 7 | True | HistoricalStructure | City | indicates that a historical structure is located within a city |
| case3_name_detail | name | 479 | True | Stadium | Stadium | indicates that a stadium has a specific name |
| case3_name_detail | nameOfGround | 659 | True | Stadium | SportsTeam | represents the relationship where a stadium is named after a sports team |
| case3_name_detail | nationalAnthem | 269 | True | Government | NationalAnthem | represents the relationship where a government holds a national anthem |
| case3_name_detail | nationality | 11 | True | Individual | Country | indicates that an individual belongs to a specific country |
| case3_name_detail | nativeOf | 477 | True | State | Bird | indicates that a state is the native home of a bird species |
| case3_name_detail | nearbyPlace | 966 | True | County | County | indicates that a county has another county nearby |
| case3_name_detail | neighbor | 138 | True | County | County | represents the relationship where a county is geographically adjacent to another county |
| case3_name_detail | netIncome | 149 | True | Company | NetIncome | represents the relationship where a companys net income is a specific financial metric |
| case3_name_detail | network | 91 | True | TV_series | BroadcastingCompany | indicates that a TV series is broadcasted by a broadcasting company |
| case3_name_detail | nickname | 88 | True | SportsTeam | Nickname | represents the relationship where a sports team has a distinctive nickname |
| case3_name_detail | northNeighbour | 165 | True | County | County | indicates that a county is geographically located north of another county |
| case3_name_detail | numberOfDoctoralStudents | 482 | True | University | Number_of_DoctoralStudents | indicates that a university has a specific number of doctoral students |
| case3_name_detail | numberOfEmployees | 114 | True | Company | Number | indicates that a company has a specific number of employees |
| case3_name_detail | numberOfMembers | 5 | True | SportsTeam | Number | indicates that a sports team has a specific number of members |
| case3_name_detail | numberOfPages | 72 | True | Book | Pages | indicates that a book has a specific number of pages |
| case3_name_detail | numberOfPostgraduateStudents | 1075 | True | University | PostgraduateStudents | represents the relationship where a university has a specific number of postgraduate students |
| case3_name_detail | numberOfPostgraduates | 654 | True | EducationalInstitution | StudentCount | indicates that an educational institution has a specific number of postgraduate students |
| case3_name_detail | numberOfStaffMembers | 448 | True | University | NumberOfStaffMembers | indicates that a university has a specific number of staff members |
| case3_name_detail | numberOfStudents | 66 | True | University | StudentCount | indicates that a university has a total count of students including various levels and staff members |
| case3_name_detail | numberOfUndergraduateStudents | 118 | True | University | Number | indicates that a university has a specific count of undergraduate students |
| case3_name_detail | occupation | 13 | True | MilitaryPerson | MilitaryOccupation | indicates that a military person holds a specific military role |
| case3_name_detail | offersServices | 737 | True | Company | WebServices | represents the relationship where a company provides services related to the World Wide Web |
| case3_name_detail | offersSport | 556 | True | EducationalInstitution | Activity | indicates that an educational institution offers a specific sport |
| case3_name_detail | officeHolder | 28 | True | Politician | Politician | indicates that a politician holds a position equivalent to another politician |
| case3_name_detail | officialLanguage | 183 | True | State | OfficialLanguage | represents the relationship where a state has a primary official language |
| case3_name_detail | officialName | 1162 | True | Nation | OfficialName | represents the relationship where a nations official name is its primary identifier |
| case3_name_detail | operatedBy | 10 | True | Airbase | MilitaryBranch | indicates that an airbase is managed by a military branch |
| case3_name_detail | operates | 51 | True | Airline | Airport | indicates that an airline manages an airport facility |
| case3_name_detail | operatingArea | 802 | True | Company | Country | represents the relationship where a company operates within a specific country |
| case3_name_detail | operatingEntity | 113 | True | Airbase | MilitaryBranch | represents the relationship where an airbase is operated by a military branch |
| case3_name_detail | operatingOrganisationFor | 463 | True |  |  |  |
| case3_name_detail | operatingOrganization | 132 | True | Aerodrome | OperatingOrganization | represents the relationship where an aerodrome is managed by an operating organization |
| case3_name_detail | operator | 40 | True | Airport | AeronauticsCompany | indicates that an airport is managed by an aeronautics company |
| case3_name_detail | orbitalPeriod | 33 | True | Asteroid | OrbitalPeriod | indicates that an asteroid has a specific orbital period |
| case3_name_detail | orbital_period | 182 | True | AstronomicalBody | OrbitalPeriod | represents the relationship where an astronomical body has a specific orbital period |
| case3_name_detail | origin | 630 | True | Musician | City | indicates that a musician originates from a specific city |
| case3_name_detail | originCountry | 108 | True | Musician | Nation | indicates that a musician originates from a sovereign state |
| case3_name_detail | ownedBuilding | 588 | True | EducationalInstitution | EducationalBuilding | indicates that an educational institution owns a specific educational building |
| case3_name_detail | ownedBy | 374 | True | Structure | EducationalInstitution | indicates that a structure is owned by an educational institution |
| case3_name_detail | owner | 38 | True | EducationalFacility | EducationalInstitution | indicates that an educational institution owns a specific facility |
| case3_name_detail | owns | 112 | True | University | Structure | indicates that a university institution possesses a specific building structure |
| case3_name_detail | parent | 111 | True | Actor | Daughter | indicates that an actor has a daughter |
| case3_name_detail | parentCompany | 609 | True | Company | Company | represents the relationship where a company is the parent entity of another company |
| case3_name_detail | partOfMission | 1124 | True | Astronaut | SpaceMission | represents the relationship where an astronaut participates in a space mission |
| case3_name_detail | participatedIn | 389 | True | MilitaryPerson | SpaceMission | represents the relationship where a military person participates in a space mission |
| case3_name_detail | people | 1093 | True | Region | Nationality | represents the relationship where a region is inhabited by a specific nationality |
| case3_name_detail | peopleName | 171 | True | Nation | PeopleGroup | represents the relationship where a nation has a specific name for its people |
| case3_name_detail | periapsis | 49 | True | Asteroid | Periapsis | indicates that an asteroid has a specific periapsis distance |
| case3_name_detail | placeOfBirth | 141 | True | Individual | BirthPlace | indicates that an individual was born in a specific geographic location |
| case3_name_detail | placeOfDeath | 154 | True | HistoricalFigure | State | indicates that a historical figure died in a specific state |
| case3_name_detail | placeOfOrigin | 52 | True | Individual | State | indicates that an individuals place of origin is within a specific state |
| case3_name_detail | placeOfUpbringing | 722 | True | Individual | Country | indicates that an individual grew up in a sovereign country |
| case3_name_detail | playIn | 293 | True | SportsTeam | League | indicates that a sports team competes in a league organized by a governing body |
| case3_name_detail | playedBy | 430 | True | League | SportsTeam | indicates that a league is contested by multiple sports teams |
| case3_name_detail | playedFor | 192 | True | Athlete | SportsTeam | indicates that an athlete has previously competed for a sports team |
| case3_name_detail | playedIn | 179 | True | SportsClub | Year | indicates that a sports club participated in a competition in a specific year |
| case3_name_detail | playedInLeague | 479 | True | SportsTeam | League | represents the relationship where a sports team competes in a league |
| case3_name_detail | playedInSeason | 76 | True | SportsTeam | Year | indicates that a sports team competes in a specific season |
| case3_name_detail | playedWith | 20 | True | Musician | Band | indicates that a musician is a member of a band |
| case3_name_detail | playground | 1101 | True | SportsClub | Stadium | indicates that a sports club has a designated sports facility |
| case3_name_detail | playsFor | 162 | True | Athlete | SportsTeam | indicates that an athlete competes for a sports team |
| case3_name_detail | playsInstrument | 50 | True | Musician | MusicalInstrument | indicates that a musician uses a specific musical instrument in their performances |
| case3_name_detail | playsMusic | 607 | True | Musician | Genre | indicates that a musician performs music within a specific genre |
| case3_name_detail | population | 1 | True | City | Population | indicates that a city has a total population count |
| case3_name_detail | populationDensity | 1 | True | City | PopulationDensity | indicates that a city has a specific population density |
| case3_name_detail | populationMetro | 31 | True | City | Population | indicates that a city has a total population count within its metropolitan area |
| case3_name_detail | populationTotal | 273 | True | DemographicEntity | Population | represents the relationship where a countrys total population is specified |
| case3_name_detail | position | 217 | True | Politician | LegislativeOffice | indicates that a politician holds a legislative office position |
| case3_name_detail | postalCode | 296 | True | Village | PostalCode | represents the relationship where a village is linked to a standardized alphanumeric postal code |
| case3_name_detail | postalCodeRange | 561 | True | City | PostalCodeRange | represents the relationship where a citys postal codes are grouped within a specific range |
| case3_name_detail | postgraduateStudents | 193 | True | University | PostgraduateStudentsCount | indicates that a university has a specific number of postgraduate students enrolled |
| case3_name_detail | postgraduates | 1127 | True | EducationalInstitution | Postgraduates | indicates that an educational institution has a count of students enrolled in postgraduate programs |
| case3_name_detail | powerType | 2 | True |  |  |  |
| case3_name_detail | precedes | 100 | True | FantasyWork | FantasyWork | indicates that one work of fiction follows another in a chronological order |
| case3_name_detail | predecessorWork | 849 | True | Book | Book | indicates that one book came before another in a series |
| case3_name_detail | premieredOn | 97 | True | Program | EventDate | indicates that a program was broadcast on a specific event date |
| case3_name_detail | prequelOf | 396 | True | Book | Book | represents the relationship where one book is a prequel to another |
| case3_name_detail | presidentDuringService | 326 | True | Politician | Politician | indicates that a politician served during the presidency of another politician |
| case3_name_detail | presidentDuringTenure | 311 | True | Politician | Politician | represents the relationship where a politician serves as president during a specific tenure |
| case3_name_detail | presidentServedUnder | 429 | True | Politician | Politician | represents the relationship where a politician served under a specific president |
| case3_name_detail | previousChampion | 88 | True | SportsTeam | SportsTeam | indicates that a sports team has previously won a championship |
| case3_name_detail | previousChampions | 419 | True | League | SportsClub | represents the relationship where a league has previously been won by a sports club |
| case3_name_detail | previousPosition | 914 | True | HistoricalFigure | ProfessionalRole | indicates that a historical figure held a previous professional role |
| case3_name_detail | previousRole | 90 | True | Athlete | TeamRole | indicates that an athlete held a specific role in a previous team |
| case3_name_detail | previousTeam | 90 | True | Athlete | SportsTeam | indicates that an athlete previously played for a different sports team |
| case3_name_detail | previouslyLedBy | 1097 | True | City | Politician | represents the relationship where a city was previously governed by a political leader |
| case3_name_detail | produced | 208 | True | AutomotiveCompany | Automobile | indicates that an automotive company manufactures a specific vehicle model |
| case3_name_detail | produces | 27 | True | Company | Software | indicates that a company manufactures or develops software products |
| case3_name_detail | product | 187 | True | Company | HeatingVentilationAir Conditioning | indicates that a company produces a specific type of product |
| case3_name_detail | productionEndYear | 60 | True | Automobile | Year | indicates that an automobile ends production in a specific year |
| case3_name_detail | productionEnded | 855 | True | Automobile | Thing | represents the relationship where an automobile production ends at a particular point in time |
| case3_name_detail | productionLocation | 137 | True | Automobile | State | indicates that an automobile is manufactured in a specific state |
| case3_name_detail | productionPeriod | 281 | True | Locomotive | ProductionPeriod | indicates that a locomotive was manufactured within a specific time frame |
| case3_name_detail | productionStartYear | 60 | True | Automobile | Year | indicates that an automobile begins production in a specific year |
| case3_name_detail | publicationDate | 253 | True | FantasyNovel | PublicationDate | represents the relationship where a fantasy novel has a specific release date |
| case3_name_detail | published | 253 | True | Publisher | FantasyNovel | indicates that a publisher releases a fantasy novel into the market |
| case3_name_detail | publisher | 100 | True | FantasyWork | Publisher | indicates that a publisher is responsible for the publication of a work of fiction |
| case3_name_detail | receivedAward | 53 | True | HistoricalFigure | MilitaryAward | indicates that a historical figure has been awarded a military honor |
| case3_name_detail | region | 26 | True | Dessert | GeographicArea | indicates that a dessert is associated with a specific geographic region |
| case3_name_detail | relateto | 7 | True | County | County | indicates that two counties are geographically adjacent to each other |
| case3_name_detail | relationTo | 459 | True | Book | Book | represents the relationship where one book is related to another book |
| case3_name_detail | relationToOther | 688 | True | Actor | Daughter | represents the relationship where an actor is the father of another person |
| case3_name_detail | relationTo_Alan_Shepard | 840 | True | EducationalInstitution | Graduation | represents the relationship where an educational institution is associated with an individual completing an educational program |
| case3_name_detail | relativePositionTo | 555 | True | County | County | indicates that one county is geographically positioned relative to another county |
| case3_name_detail | releaseDate | 172 | True | Book | ReleaseDate | indicates that a book was released on a specific date |
| case3_name_detail | represented | 217 | True | Politician | State | indicates that a politician represents a specific state |
| case3_name_detail | requires | 860 | True | SweetDish | FoodItem | indicates that a dessert requires a specific food item as an ingredient |
| case3_name_detail | requiresIngredient | 1051 | True | SweetFood | BakedGood | indicates that a dessert requires a specific type of baked good as one of its ingredients |
| case3_name_detail | retiredOn | 69 | True | HistoricalFigure | Date | indicates that a historical figure retired on a specific date |
| case3_name_detail | retirementDate | 615 | True | HistoricalFigure | RetirementDate | indicates that a historical figure retires on a specific date |
| case3_name_detail | revenue | 117 | True | Company | Revenue | represents the relationship where a company generates a specific amount of income |
| case3_name_detail | role | 332 | True | Citizen | Professional | indicates that a citizen holds a specific professional role |
| case3_name_detail | rotationPeriod | 33 | True | Asteroid | RotationPeriod | indicates that an asteroid has a specific rotation period |
| case3_name_detail | rotation_period | 103 | True | Planet | Duration | indicates that a planet completes one rotation in a given duration |
| case3_name_detail | rotationalPeriod | 109 | True | Asteroid | RotationalPeriod | indicates that an asteroid rotates on its axis in a specific amount of time |
| case3_name_detail | runwayLength | 41 | True | Airport | RunwayLength | indicates that an airport has a specific runway length measurement |
| case3_name_detail | runwayMaterial | 249 | True | Aerodrome | Concrete | represents the relationship where an aerodrome runway is constructed with concrete |
| case3_name_detail | runwayName | 40 | True | Airport | RunwayName | indicates that an airport has a specific runway name for identification |
| case3_name_detail | runwaySurface | 122 | True | Aerodrome | Concrete | indicates that an aerodrome has a runway surface made of concrete |
| case3_name_detail | runwaySurfaceMaterial | 502 | True | Aerodrome | ConstructionMaterial | indicates that an aerodrome has a runway surface made of a specific construction material |
| case3_name_detail | runwaySurfaceType | 494 | True |  |  |  |
| case3_name_detail | school | 703 | True | HistoricalFigure | EducationalInstitution | indicates that a historical figure attended an educational institution |
| case3_name_detail | selectedBy | 11 | True | Individual | GovernmentAgency | indicates that an individual is selected by a governmental agency |
| case3_name_detail | selectedYear | 337 | True | HistoricalFigure | SelectionYear | indicates that a historical figure was selected in a specific year |
| case3_name_detail | selectionYear | 11 | True | GovernmentAgency | Year | indicates that a governmental agency selects individuals in a specific year |
| case3_name_detail | sells | 22 | True | PharmaceuticalCompany | PersonalCareProduct | indicates that a pharmaceutical company offers personal care products |
| case3_name_detail | sequelTo | 307 | True | Book | Book | indicates that one book follows another in a series |
| case3_name_detail | servedAs | 19 | True | DessertFood | Dessert | indicates that a dessert food item is specifically prepared as a sweet course at the end of a meal |
| case3_name_detail | servedAt | 485 | True | SweetDish | DessertCourse | indicates that a sweet dish is served as part of a dessert course |
| case3_name_detail | servedBy | 1155 | True | Aerodrome | Autodrome | represents the relationship where an aerodrome is managed by an autodrome |
| case3_name_detail | serves | 56 | True | Aerodrome | Autodrome | indicates that an aerodrome facilitates the use of another facility |
| case3_name_detail | servesAs | 569 | True | Nation | SweetDish | indicates that a nation is associated with a particular sweet dish |
| case3_name_detail | serviceBranch | 154 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure served in a specific military branch |
| case3_name_detail | shownBy | 388 | True | Film | BroadcastingCompany | indicates that a film is broadcasted by a specific broadcasting company |
| case3_name_detail | singsIn | 716 | True | Musician | Band | represents the relationship where a musician is a member of a musical group |
| case3_name_detail | southeastNeighbor | 501 | True | AdministrativeDivision | AdministrativeDivision | indicates that an administrative division is geographically located to the southeast of another |
| case3_name_detail | southeastNeighbour | 165 | True | County | County | indicates that a county is geographically located southeast of another county |
| case3_name_detail | southeast_of | 104 | True | County | County | indicates that one county is located southeast of another county |
| case3_name_detail | southwestNeighbour | 165 | True | County | County | indicates that a county is geographically located southwest of another county |
| case3_name_detail | sportsOffered | 522 | True | EducationalInstitution | RecreationalSport | indicates that an educational institution offers a recreational sport |
| case3_name_detail | spouse | 28 | True | Politician | Individual | indicates that a politician is married to an individual |
| case3_name_detail | staffCount | 871 | True | University | StaffCount | indicates that a university has a total number of staff members employed |
| case3_name_detail | staffMembers | 66 | True | University | StaffMembers | indicates that a university has a specific number of individuals employed by the institution |
| case3_name_detail | staffSize | 257 | True | University | StaffSize | indicates that a university has a specific number of staff members |
| case3_name_detail | staffTotal | 768 | True | University | StaffTotal | indicates that a university has a total number of staff members |
| case3_name_detail | starredBy | 867 | True | TelevisionShow | Actor | indicates that a television show features a specific actor |
| case3_name_detail | starredIn | 472 | True | Actor | Broadcast | represents the relationship where an actor participates in a broadcast program |
| case3_name_detail | starring | 91 | True | TV_series | Individual | indicates that a TV series features individual actors |
| case3_name_detail | starringIn | 1133 | True | Actor | TVShow | indicates that an Actor is a key performer in a TVShow |
| case3_name_detail | startDate | 997 | True | EducationalFacility | TemporalEntity | indicates that an educational facility was constructed on a specific date |
| case3_name_detail | startDateConstruction | 112 | True | Structure | Year | indicates that construction on a building began on a specific year |
| case3_name_detail | startDateOfCareer | 523 | True | TranceMusician | Year | indicates that a trance musician begins their career in a specific year |
| case3_name_detail | startedPerforming | 20 | True | Musician | Date | indicates that a musician began performing at a specific date |
| case3_name_detail | state | 548 | True | AdministrativeDivision | AdministrativeDivision | represents the relationship where an administrative division belongs to a state |
| case3_name_detail | stateOfDeath | 533 | True | Politician | State | indicates that a politician died in a specific state |
| case3_name_detail | status | 146 | True | EducationalInstitution | EducationalStatus | indicates that an educational institution is recognized with a specific designation by a regulatory body |
| case3_name_detail | statusGrantedBy | 406 | True | EducationalInstitution | RegulatoryBody | indicates that an educational institution has been granted a status by a regulatory body |
| case3_name_detail | studentBody_size | 379 | True | University | StudentBody_size | represents the relationship where a university has a total student body size |
| case3_name_detail | studentCount_Doctoral | 871 | True | University | StudentCount_Doctoral | indicates that a university has a specific number of doctoral students enrolled |
| case3_name_detail | studentCount_Postgraduate | 871 | True | University | StudentCount_Postgraduate | indicates that a university has a specific number of postgraduate students enrolled |
| case3_name_detail | studentCount_Undergraduate | 871 | True | University | StudentCount_Undergraduate | indicates that a university has a specific number of undergraduate students enrolled |
| case3_name_detail | studentType | 871 | True |  |  |  |
| case3_name_detail | students | 579 | True | University | Students | indicates that a university has a total number of students enrolled |
| case3_name_detail | studiedAt | 964 | True | Photographer | EducationalInstitution | indicates that a photographer pursued formal education at an applied arts school |
| case3_name_detail | studiesAt | 36 | True | Person | EducationalInstitution | Indicates that a person studies at an educational institution. |
| case3_name_detail | succeeded | 353 | True | Politician | Politician | indicates that one politician replaces another in a political leadership role |
| case3_name_detail | succeededBy | 429 | True | Politician | Politician | indicates that one politician succeeded another in a political role |
| case3_name_detail | successor | 152 | True | Politician | Politician | represents the relationship where one politician succeeds another in a political role |
| case3_name_detail | support | 610 | True | University | StudentPopulation | indicates that a university institution provides support services to a student body |
| case3_name_detail | team | 42 | True | Player | Team | indicates that a player competes with a specific team |
| case3_name_detail | teamLocation | 700 | True | Athlete | Stadium | indicates that an athletes team is based at a specific stadium |
| case3_name_detail | technicalCampusAffiliation | 685 | True | EducationalInstitution | RegulatoryBody | indicates that an educational institution is affiliated with a regulatory body responsible for technical education |
| case3_name_detail | technicalCampusStatus | 978 | True | EducationalInstitution | GrantStatus | represents the relationship where an educational institution is granted a specific status by a regulatory body |
| case3_name_detail | timeZone | 73 | True | City | Timezone | indicates that a city operates within a specific time zone |
| case3_name_detail | timezone | 61 | True | City | StandardTimezone | indicates that a city operates under a specific time zone |
| case3_name_detail | toTheSouthEastOf | 107 | True | County | County | indicates that one county is located to the southeast of another county |
| case3_name_detail | tookPartIn | 151 | True | Astronaut | SpaceMission | represents the relationship where an astronaut engages in a space-related activity |
| case3_name_detail | totalArea | 802 | True | Country | Area | indicates that a country has a specific total area |
| case3_name_detail | totalNumberOfStudents | 136 | True | University | TotalNumberOfStudents | indicates that a university has a comprehensive student body count |
| case3_name_detail | totalStudents | 352 | True | University | TotalStudents | indicates that a university has a total number of enrolled students |
| case3_name_detail | type | 7 | True |  |  |  |
| case3_name_detail | undergraduateCount | 610 | True | StudentPopulation | UndergraduateCount | represents the relationship where a student population includes a specific count of undergraduate students |
| case3_name_detail | undergraduateStudentPopulation | 932 | True | University | StudentPopulation | indicates that a university has a specific number of undergraduate students |
| case3_name_detail | undergraduateStudents | 66 | True | University | UndergraduateStudents | indicates that a university has a specific number of students enrolled in undergraduate programs |
| case3_name_detail | undergraduateTotal | 768 | True | University | UndergraduateTotal | indicates that a university has a specific number of undergraduate students |
| case3_name_detail | undergraduates | 1127 | True | EducationalInstitution | Undergraduates | indicates that an educational institution has a count of students enrolled in undergraduate programs |
| case3_name_detail | utcOffset | 1 | True | City | UTCOffset | indicates that a city has a UTC offset |
| case3_name_detail | wasAMemberOf | 1049 | True | Astronaut | SpaceMission | indicates that an astronaut participates in a specific spaceflight mission |
| case3_name_detail | wasFoundedBy | 221 | True | BroadcastingCompany | FoundingEntity | indicates that a broadcasting company was founded by a specific founding entity |
| case3_name_detail | wasInOfficeWhile | 728 | True | Individual | Presidency | indicates that an individual held a position during a specific presidency |
| case3_name_detail | wasOn | 375 | True | MilitaryPerson | SpaceMission | indicates that a military person participated in a space mission |
| case3_name_detail | wasPartOf | 639 | True | Astronaut | SpaceMission | indicates that an astronaut participates in a space mission |
| case3_name_detail | weight | 46 | True | Individual | Weight | indicates that an individuals weight is measured |
| case3_name_detail | westNeighbor | 501 | True | AdministrativeDivision | AdministrativeDivision | indicates that an administrative division is geographically located to the west of another |
| case3_name_detail | winLeague | 128 | True | SportsTeam | League | indicates that a sports team has won a league |
| case3_name_detail | winLeagueTitle | 498 | True | SportsTeam | ProfessionalLeague | indicates that a sports team has won a league title |
| case3_name_detail | winningLeague | 179 | True | SportsClub | League | indicates that a sports club won a league |
| case3_name_detail | wonChampionship | 293 | True | SportsTeam | League | indicates that a sports team achieved victory in a league organized by a governing body |
| case3_name_detail | wonLeague | 76 | True | SportsTeam | League | indicates that a sports team has won a league championship |
| case3_name_detail | wonLeagueChampionship | 189 | True | SportsTeam | Year | indicates that a sports team won a league championship in a specific year |
| case3_name_detail | wrote | 351 | True | Author | Book | represents the relationship where an author creates a book |
| case3_name_detail | year | 82 | True | League | Year | indicates that a league takes place in a specific year |
| case3_name_detail | yearBegunCareer | 595 | True | Musician | Year | indicates that a musician began their musical career in a specific year |
| case3_name_detail | yearErected | 247 | True | HistoricalMonument | Year | represents the relationship where a monument is associated with a specific year of erection |
| case3_name_detail | yearInLeague | 128 | True | SportsTeam | Year | indicates that a sports team has been in a league for a specific year |
| case3_name_detail | yearInPosition | 242 | True | HistoricalFigure | YearInPosition | indicates that a historical figure served in a leadership role for a specific year |
| case3_name_detail | yearOfBirth | 909 | True | Individual | Year | indicates that an individual was born in a specific year |
| case3_name_detail | yearOfConstruction | 836 | True | Monument | Year | indicates that a monument was constructed in a specific year |
| case3_name_detail | yearOfDeath | 909 | True | Individual | Year | indicates that an individual died in a specific year |
| case3_name_detail | yearOfGraduation | 557 | True | Historian | Year | indicates that a historian graduated from their educational institution in a specific year |
| case3_name_detail | youthClub | 101 | True | Athlete | SportsTeam | indicates that an athlete is a member of the youth team of a sports club |
| case3_name_detail | youthFootballClub | 1026 | True | Athlete | YouthFootballClub | indicates that an athlete was initially nurtured by a youth football club |
| case3_name_detail | youthSideOf | 162 | True | Athlete | SportsTeam | indicates that an athlete is part of a youth team of a sports team |
| case3_name_detail | youthTeam | 192 | True | SportsTeam | Athlete | indicates that a sports team has an affiliated youth athlete |
| case4_detail_strict | CEO | 465 | True | Company | CEO | indicates that a company is led by a chief executive officer |
| case4_detail_strict | aboveSeaLevel | 925 | True | City | AboveSeaLevel | indicates that a city is located above a certain sea level |
| case4_detail_strict | absoluteMagnitude | 33 | True | Asteroid | AbsoluteMagnitude | indicates that an asteroid has a specific absolute magnitude |
| case4_detail_strict | absolute_magnitude | 447 | True | CelestialBody | AbsoluteMagnitude | represents the relationship where an asteroid has a specific brightness measurement |
| case4_detail_strict | actedIn | 111 | True | Actor | TelevisionSeries | indicates that an actor starred in a television series |
| case4_detail_strict | address | 3 | True | ArchitecturalStructure | GeographicLocation | indicates that an architectural structure has a specific physical address |
| case4_detail_strict | affiliatedTo | 974 | True | EducationalInstitution | University | indicates that an educational institution is associated with a university |
| case4_detail_strict | affiliatedWith | 254 | True | EducationalCouncil | University | indicates that an educational council is associated with a university institution |
| case4_detail_strict | affiliation | 17 | True | Institute | University | indicates that an educational institution is associated with a university for academic purposes |
| case4_detail_strict | airedOn | 124 | True | TVSeries | BroadcastingCompany | indicates that a TV series is broadcasted by a specific broadcasting company |
| case4_detail_strict | airedShowOn | 345 | True | BroadcastingCompany | EventDate | indicates that a broadcasting company aired a show on a specific date |
| case4_detail_strict | altitudeAboveSeaLevel | 15 | True | Airport | Altitude | indicates that an airport is at a specific altitude above sea level |
| case4_detail_strict | annualRevenue | 1157 | True | Company | AnnualRevenue | represents the total revenue generated by a company in a fiscal year |
| case4_detail_strict | anthem | 225 | True | Monarchy | NationalAnthem | represents the relationship where a monarchy has a national anthem |
| case4_detail_strict | apoapsis | 33 | True | Asteroid | Apoapsis | indicates that an asteroid has a specific apoapsis distance |
| case4_detail_strict | architect | 3 | True | ArchitecturalStructure | Architect | indicates that an architectural structure is designed by a professional architect |
| case4_detail_strict | are | 826 | True | Thing | Thing | indicates that a group of entities share a common identity or classification |
| case4_detail_strict | area | 200 | True | Country | Area | represents the relationship where a countrys geographical extent is quantified |
| case4_detail_strict | areaCode | 74 | True | Place | AreaCode | represents the relationship where a place is uniquely identified by a numeric area code |
| case4_detail_strict | assembledIn | 994 | True | Automobile | City | indicates that an automobile is manufactured in a specific city |
| case4_detail_strict | assemblyLineLocation | 39 | True | Vehicle | City | indicates that a vehicle was produced on an assembly line located within a city |
| case4_detail_strict | assemblyLocation | 409 | True | Automobile | City | represents the relationship where a vehicle is produced in a city |
| case4_detail_strict | associatedBand | 721 | True | Musician | MusicalGroup | indicates that a musician is associated with a musical group |
| case4_detail_strict | associatedWith | 400 | True | Musician | Musician | indicates that a musician collaborates with another artist in musical projects |
| case4_detail_strict | attendedSchool | 63 | True | Student | EducationalInstitution | represents the relationship where a student is enrolled in an educational institution |
| case4_detail_strict | author | 72 | True | Book | Author | indicates that a book is authored by an individual |
| case4_detail_strict | awarded | 599 | True | HistoricalFigure | Medal | represents the relationship where a historical figure receives a distinguished service medal |
| case4_detail_strict | awardedBy | 349 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure received a military award from a branch of the armed forces |
| case4_detail_strict | awardedTechnicalCampusStatusTo | 131 | True | GovernmentAgency | EducationalInstitution | represents the relationship where a government agency grants a technical campus status to an educational institution |
| case4_detail_strict | awardedTo | 154 | True | MilitaryBranch | HistoricalFigure | indicates that a military branch awards a specific historical figure a medal |
| case4_detail_strict | awardingBody | 1044 | True | Individual | MilitaryBranch | indicates that an individual is awarded by a specific military branch |
| case4_detail_strict | becameProfessional | 582 | True | Individual | Profession | indicates that an individual transitioned into a professional role |
| case4_detail_strict | beganMusicalCareer | 400 | True | Musician | Year | represents the relationship where a musician starts their professional music career |
| case4_detail_strict | birthDate | 13 | True | MilitaryPerson | Date | indicates that a military person was born on a specific date |
| case4_detail_strict | birthPlace | 13 | True | MilitaryPerson | City | indicates that a military person is born in a specific city |
| case4_detail_strict | birthYear | 34 | True | HistoricalFigure | Year | indicates that a historical figure was born in a specific year |
| case4_detail_strict | bodyStyle | 399 | True | Automobile | BodyStyle | represents the relationship where an automobile has a specific body style |
| case4_detail_strict | borderingCounty | 906 | True | County | County | indicates that a county shares borders with other counties |
| case4_detail_strict | born | 364 | True | Astronaut | BirthDate | indicates that an astronaut was born on a specific date |
| case4_detail_strict | bornIn | 4 | True | Individual | City | indicates that an individual is born in a specific city |
| case4_detail_strict | bornOn | 30 | True | Athlete | BirthDate | indicates that an athlete was born on a specific date |
| case4_detail_strict | bornWithin | 357 | True | Individual | Monarchy | indicates that an individual was born within a monarchy |
| case4_detail_strict | born_on | 805 | True | Astronaut | BirthDate | indicates that an astronaut was born on a specific date |
| case4_detail_strict | broadcastedBy | 6 | True | TVShow | BroadcastingCompany | indicates that a TV show is broadcast by a specific broadcasting company |
| case4_detail_strict | broughtUpBy | 250 | True | MediaCompany | AnimatedCharacter | represents the relationship where a media company is associated with a specific animated character |
| case4_detail_strict | builder | 105 | True | Locomotive | Company | represents the relationship where a locomotive is produced by a manufacturing company |
| case4_detail_strict | built | 966 | True | HistoricalStructure | Year | indicates that a historical structure was constructed in a specific year |
| case4_detail_strict | builtBetween | 150 | True | Locomotive | HistoricalPeriod | indicates that a locomotive was constructed within a specific historical time frame |
| case4_detail_strict | builtBy | 757 | True | EducationalBuilding | Architect | represents the relationship where an educational building is designed by an architect |
| case4_detail_strict | builtIn | 7 | True | HistoricalStructure | TimePeriod | indicates that a historical structure is constructed in a specific year |
| case4_detail_strict | builtOn | 278 | True | EducationalBuilding | ConstructionDate | indicates that an educational building was constructed on a specific date |
| case4_detail_strict | campusLocation | 410 | True | University | Road | indicates that a university is situated on a specific road within its campus |
| case4_detail_strict | campusStatus | 974 | True | EducationalInstitution | CampusStatus | indicates that an educational institution has been granted a specific status by a governing body |
| case4_detail_strict | campus_location | 563 | True | EducationalInstitution | Address | indicates that an educational institution has a specific campus location |
| case4_detail_strict | canBeVaryWith | 67 | True | Dessert | DairyProduct | indicates that a dessert can be prepared with a dairy product |
| case4_detail_strict | categorization | 501 | True | HistoricalStructure | HistoricResource | indicates that a historical structure is recognized as a resource contributing to the significance of a district |
| case4_detail_strict | category | 129 | True |  |  |  |
| case4_detail_strict | ceremonialCounty | 830 | True | Town | CeremonialCounty | represents the relationship where a town is part of a ceremonial county |
| case4_detail_strict | championOf | 659 | True | SportsTeam | League | represents the relationship where a sports team is the champion of a league |
| case4_detail_strict | champions | 16 | True | SportsTeam | League | indicates that a sports team is the champion of a league |
| case4_detail_strict | championships | 629 | True | SportsTeam | Number | indicates that a sports team has won a specific number of championships |
| case4_detail_strict | channel | 384 | True | TVSeries | BroadcastingCompany | indicates that a TV series is broadcasted on a specific television channel operated by a broadcasting company |
| case4_detail_strict | citizens | 369 | True | Nation | Population | represents the relationship where a nation comprises a specific demographic group |
| case4_detail_strict | citizenship | 326 | True | Politician | Citizen | indicates that a politician holds a specific citizenship status |
| case4_detail_strict | city | 418 | True | EducationalInstitution | City | indicates that an educational institution is located in a specific city |
| case4_detail_strict | coach | 295 | True | Team | Coach | represents the relationship where a coach leads a sports team |
| case4_detail_strict | competedIn | 284 | True | SportsTeam | Season | represents the relationship where a sports team participated in a specific season |
| case4_detail_strict | completedOn | 190 | True | ArchitecturalStructure | CompletionDate | indicates that an architectural structure is finished on a specific completion date |
| case4_detail_strict | completionDate | 112 | True | Structure | Year | indicates that a building was completed on a specific year |
| case4_detail_strict | constructionPeriod | 47 | True | Structure | Period | indicates that a structure was built within a specific time frame |
| case4_detail_strict | constructionStart | 361 | True | Facility | Temporal | indicates that a facilitys construction began on a specific date |
| case4_detail_strict | constructionStartDate | 1121 | True | EducationalBuilding | ConstructionStartDate | indicates that an educational building has a specific start date for construction |
| case4_detail_strict | contains | 104 | True | County | HistoricalStructure | indicates that a county includes a historical structure within its boundaries |
| case4_detail_strict | containsAdministrativeTerritory |  | False | AdministrativeTerritory | AdministrativeTerritory | Indicates that an administrative territory contains another administrative territory. |
| case4_detail_strict | containsIngredient | 986 | True | Dish | Nutrition | indicates that a dish includes granola, shredded coconut, and raisins as nutritional ingredients |
| case4_detail_strict | containsSettlement |  | False | AdministrativeTerritory | Settlement | Indicates that an administrative territory contains a settlement such as a city or town. |
| case4_detail_strict | containsTeam | 284 | True | League | SportsTeam | represents the relationship where a league includes multiple sports teams |
| case4_detail_strict | corporateForm | 29 | True | Company | LegalForm | represents the relationship where a company has a specific legal form |
| case4_detail_strict | cosparId | 416 | True | SpaceMission | CosparId | represents the relationship where a space mission is uniquely identified by a COSPAR ID |
| case4_detail_strict | country | 3 | True | EducationalInstitution | Country | indicates that an educational institution is located in a specific country |
| case4_detail_strict | countryOfBirth | 356 | True | HistoricalFigure | Country | represents the relationship where a historical figure is born in a specific country |
| case4_detail_strict | countryOfCitizenship | 344 | True | Politician | Country | indicates that a politician is a citizen of a specific country |
| case4_detail_strict | countryOfOrigin | 674 | True | AutomobileCompany | Nation | represents the relationship where an automobile company is founded in a particular nation |
| case4_detail_strict | countryOrigin | 369 | True | Sweet | Nation | indicates that a sweet dessert originates from a specific nation |
| case4_detail_strict | county | 7 | True | HistoricalStructure | County | indicates that a historical structure is situated within a county |
| case4_detail_strict | created | 562 | True | Creator | AnimatedCharacter | indicates that a creator produces an animated character |
| case4_detail_strict | creator | 6 | True | TVShow | Creator | represents the relationship where a TV show is created by a specific creator |
| case4_detail_strict | crewMemberOf | 827 | True | Astronaut | SpaceMission | represents the relationship where an astronaut serves as a crew member on a space mission |
| case4_detail_strict | currency | 24 | True | GeopoliticalEntity | MonetaryUnit | indicates that a country uses a specific currency for transactions |
| case4_detail_strict | currentAssemblyLocation | 697 | True | Automobile | City | indicates that an automobile is currently assembled in a specific city |
| case4_detail_strict | currentClub | 30 | True | Athlete | FootballClub | indicates that an athlete is currently affiliated with a football club |
| case4_detail_strict | currentLeader | 699 | True | Nation | Politician | represents the relationship where a nation is led by a political leader |
| case4_detail_strict | currentLocation | 187 | True | Company | Country | indicates that a company is headquartered in a specific country |
| case4_detail_strict | currentPosition | 156 | True | Politician | PoliticalOffice | represents the relationship where a politician holds a current political office position |
| case4_detail_strict | currentSenator | 476 | True | State | Politician | represents the relationship where a state is governed by a current senator |
| case4_detail_strict | currentTeam | 42 | True | Player | Team | represents the relationship where a player is currently associated with a specific team |
| case4_detail_strict | currentTenants | 3 | True | ArchitecturalStructure | EducationalInstitution | indicates that an architectural structure is currently occupied by an educational institution |
| case4_detail_strict | currentlyPlaysFor | 450 | True | Athlete | SportsTeam | indicates that an athlete is currently playing for a specific sports team |
| case4_detail_strict | cylinderCount | 878 | True | Locomotive | CylinderCount | indicates that a locomotive has a specific number of cylinders |
| case4_detail_strict | dateOfBirth | 25 | True | Individual | BirthDate | indicates that an individual has a specific birth date |
| case4_detail_strict | dateOfDeath | 173 | True | Individual | DeathDate | indicates that an individual died on a specific date |
| case4_detail_strict | deathCause | 640 | True | Individual | Death | indicates that an individuals death is caused by a natural or medical condition |
| case4_detail_strict | deathDate | 93 | True | Individual | DeathDate | indicates that an individual has a specific death date |
| case4_detail_strict | deathPlace | 28 | True | Politician | Nation | indicates that a politician died in a specific nation |
| case4_detail_strict | debutTeam | 425 | True | Player | Team | indicates that a player made their initial appearance for a specific team |
| case4_detail_strict | degree | 477 | True | EducationalInstitution | Degree | indicates that an educational institution awarded a specific degree |
| case4_detail_strict | designatedAs | 643 | True | EducationalInstitution | CampusDesignation | represents the relationship where an educational institution is given a specific designation or classification |
| case4_detail_strict | designatedTechnicalCampusStatusTo | 143 | True | Council | Institute | indicates that a council formally recognizes a technical education institution as a campus |
| case4_detail_strict | diedDateTime | 991 | True | Individual | DateTime | indicates that an individual died on a specific date and time |
| case4_detail_strict | diedIn | 4 | True | Individual | Country | indicates that an individual dies in a specific country |
| case4_detail_strict | direction | 365 | True | AdministrativeDivision | GeographicalDirection | indicates that a territorial division is geographically positioned relative to another |
| case4_detail_strict | director | 131 | True | EducationalInstitution | Educator | represents the relationship where an educational institution is led by an educator |
| case4_detail_strict | discovered | 182 | True | Astronomer | AstronomicalBody | indicates that an astronomer identifies a celestial body |
| case4_detail_strict | discoveredBy | 33 | True | Asteroid | Astronomer | indicates that an asteroid is identified by an astronomer |
| case4_detail_strict | discoveryDate | 33 | True | Asteroid | Date | indicates that an asteroids discovery is recorded with a specific date |
| case4_detail_strict | doctoralStudentPopulation | 932 | True | University | StudentPopulation | indicates that a university has a specific number of doctoral students |
| case4_detail_strict | doctoralStudents | 66 | True | University | DoctoralStudents | indicates that a university has a specific number of students enrolled in doctoral programs |
| case4_detail_strict | draftPick | 518 | True | Athlete | DraftPick | indicates that an athlete is selected as a draft pick |
| case4_detail_strict | draftPickNumber | 1057 | True | Athlete | DraftPickNumber | indicates that an athlete is assigned a draft pick number |
| case4_detail_strict | earnings | 85 | True | Company | Earnings | indicates that a company generates financial income over a year |
| case4_detail_strict | eat | 790 | True | Dessert | Type | indicates that a dessert is consumed as a type of food |
| case4_detail_strict | educatedAt | 707 | True | FootballClub | Athlete | indicates that a football club has an athlete as a former member |
| case4_detail_strict | educates | 687 | True | University | StudentPopulation | indicates that a university enrolls a total number of students |
| case4_detail_strict | education | 53 | True | HistoricalFigure | Degree | indicates that a historical figure has earned a formal academic degree |
| case4_detail_strict | elevationAboveSeaLevel | 41 | True | Airport | ElevationAboveSeaLevel | indicates that an airport has a specific elevation above sea level measurement |
| case4_detail_strict | endedManufacturingOf | 325 | True | Automaker | AutomobileModel | indicates that an automaker ceases production of a specific vehicle model |
| case4_detail_strict | engine | 350 | True | Locomotive | Engine | indicates that a locomotive is equipped with a particular type of engine |
| case4_detail_strict | engineConfiguration | 749 | True | Locomotive | EngineConfiguration | indicates that a locomotive employs a particular engine configuration |
| case4_detail_strict | enrollment | 70 | True | University | StudentCount | represents the relationship where a university has a specific number of students enrolled |
| case4_detail_strict | epoch | 64 | True | Asteroid | Time | represents the relationship where an asteroid reaches a specific epoch in its orbit |
| case4_detail_strict | epochDate | 958 | True | CelestialBody | Date | indicates that a celestial body has a specific reference date |
| case4_detail_strict | erectedIn | 638 | True | Monument | State | indicates that a monument is erected in a specific state |
| case4_detail_strict | established | 104 | True | HistoricalStructure | Year | indicates that a historical structure was founded in a specific year |
| case4_detail_strict | establishedIn | 146 | True | EducationalInstitution | Year | indicates that an educational institution was founded in a specific year |
| case4_detail_strict | establishmentYear | 138 | True | Monument | Year | indicates that a monument was established in a specific year |
| case4_detail_strict | ethnicGroup | 4 | True | Country | Group | represents the relationship where a country has a specific ethnic group |
| case4_detail_strict | extinctionDate | 558 | True | AutomobileBrand | Year | represents the relationship where an automobile brand ceased operations on a specific year |
| case4_detail_strict | firstAired | 6 | True | TVShow | EventDate | indicates that a TV show marks its premiere on a specific date |
| case4_detail_strict | firstAiredBy | 698 | True | TelevisionShow | BroadcastingCompany | indicates that a television show is broadcasted by a specific broadcasting company |
| case4_detail_strict | firstAiredOn | 672 | True | TVSeries | EventDate | indicates that a TVSeries has a specific event date of its premiere |
| case4_detail_strict | firstAppearance | 260 | True | Film | AnimatedCharacter | represents the relationship where a film features its initial appearance of an animated character |
| case4_detail_strict | firstAppearedAsFilmCharacterIn | 779 | True | FilmCharacter | Film | represents the relationship where a characters first appearance in a film is specified |
| case4_detail_strict | firstAppearedIn | 824 | True | AnimatedCharacter | Film | represents the relationship where an animated characters debut is in a movie |
| case4_detail_strict | firstBroadcast | 250 | True | AnimatedCharacter | EventDate | indicates that an animated character had its first broadcast on a specific date |
| case4_detail_strict | firstProducedIn | 199 | True | Automobile | Year | indicates that an automobile was first manufactured in a specific year |
| case4_detail_strict | firstProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was first manufactured in a specific year |
| case4_detail_strict | followedBy | 241 | True | Book | Book | indicates that one book series continues another in a narrative sequence |
| case4_detail_strict | follows | 585 | True | Book | Book | indicates that one book comes after another in a series |
| case4_detail_strict | foodServedAsDessert | 811 | True | Nation | Dessert | indicates that a nation serves a specific dessert as a dessert |
| case4_detail_strict | formerClub | 616 | True | Player | FootballClub | represents the relationship where a player was previously affiliated with a football club |
| case4_detail_strict | formerTeam | 186 | True | Player | Team | represents the relationship where a player was formerly part of a team |
| case4_detail_strict | formerlyPlayedFor | 782 | True | Athlete | SportsTeam | indicates that an athlete previously played for a sports team |
| case4_detail_strict | formerlyPlayedWith | 318 | True | Athlete | SportsTeam | indicates that an athlete previously played for a sports team |
| case4_detail_strict | foundIn | 19 | True | DessertFood | Country | represents the relationship where a dessert food item is located within a specific country |
| case4_detail_strict | founded | 114 | True | Company | Date | indicates that a company was established on a specific date |
| case4_detail_strict | foundedBy | 120 | True | Company | Founder | represents the relationship where a company is initiated by a person |
| case4_detail_strict | founder | 62 | True | Company | Founder | represents the relationship where a company is initiated and managed by a founder |
| case4_detail_strict | founding | 691 | True | City | HistoricalFigure | represents the relationship where a city is founded by a historical figure |
| case4_detail_strict | foundingDate | 22 | True | PharmaceuticalCompany | FoundingDate | indicates that a pharmaceutical company was established on a specific founding date |
| case4_detail_strict | foundingEntity | 221 | True | BroadcastingCompany | FoundingEntity | represents the relationship where a broadcasting company is established by a founding entity |
| case4_detail_strict | foundingFather | 1014 | True | BroadcastingCompany | FoundingFather | represents the relationship where a broadcasting company was established by a founding father |
| case4_detail_strict | foundingPerson | 831 | True | Company | Founder | indicates that a company was founded by a specific person |
| case4_detail_strict | foundingPlace | 114 | True | Company | City | indicates that a company was founded in a specific city |
| case4_detail_strict | foundingYear | 1024 | True | Aerodrome | Year | indicates that an aerodrome was founded in a specific year |
| case4_detail_strict | from | 936 | True | Musician | Thing | indicates that a musician is associated with a specific geographic entity |
| case4_detail_strict | fullName | 203 | True | State | Name | indicates that a state has a formal name |
| case4_detail_strict | full_name | 246 | True | SportsTeam | SportsTeam | indicates that a sports team has a formal name |
| case4_detail_strict | gaveStatusBy | 857 | True | EducationalInstitution | EducationalAuthority | indicates that an educational institution is granted a status by an educational authority |
| case4_detail_strict | genre | 91 | True | TV_series | Series | indicates that a TV series belongs to a specific series category |
| case4_detail_strict | governingBody | 748 | True | City | Position | indicates that a city is governed by a specific leadership position |
| case4_detail_strict | governmentForm | 1036 | True | StateFormOfGovernment | UnitaryState | indicates that a state form of government is characterized by a centralized system of governance |
| case4_detail_strict | governmentType | 1 | True |  |  |  |
| case4_detail_strict | governor | 925 | True | City | GovernmentBody | indicates that a city is governed by a government body |
| case4_detail_strict | graduatedFrom | 557 | True | Historian | Institution | indicates that a historian received their education from an academic institution |
| case4_detail_strict | graduatedIn | 1044 | True | Individual | Year | indicates that an individual completes an educational program by a specific year |
| case4_detail_strict | graduationYear | 242 | True | HistoricalFigure | GraduationYear | indicates that a historical figure completed an educational program in a specific year |
| case4_detail_strict | ground | 16 | True | Stadium | SportsTeam | indicates that a stadium hosts a sports team |
| case4_detail_strict | hadCampusIn | 492 | True | University | City | indicates that a university had its campus within a specific city |
| case4_detail_strict | has | 48 | True | AdministrativeDivision | AdministrativeDivision | indicates that a territorial division contains another territorial division |
| case4_detail_strict | hasBird | 282 | True | State | Species | represents the relationship where a state is associated with a specific bird species |
| case4_detail_strict | hasDessert | 791 | True | City | SweetDish | indicates that a city has a specific dessert dish |
| case4_detail_strict | hasFood | 945 | True | Nation | Dessert | indicates that a nation includes a specific type of food in its culinary offerings |
| case4_detail_strict | hasIngredient | 892 | True | Dessert | Ingredient | indicates that a dessert contains a specific ingredient |
| case4_detail_strict | hasItem | 171 | True | UrbanCenter | SweetFood | represents the relationship where an urban center has another specific type of sweet food item |
| case4_detail_strict | hasMember | 360 | True | Band | Musician | represents the relationship where a band comprises a musician |
| case4_detail_strict | hasNativeBird | 505 | True | State | Bird | represents the relationship where a state is home to a specific native bird species |
| case4_detail_strict | hasOfficial | 493 | True | State | Official | represents the relationship where a state appoints an official to lead its administration |
| case4_detail_strict | hasPart | 727 | True | GeographicArea | GeographicArea | represents the relationship where one geographic area contains another |
| case4_detail_strict | hasPopulationDensity | 669 | True | Country | PopulationDensity | represents the relationship where a country has a specific population density |
| case4_detail_strict | hasProperty | 836 | True | City | Monument | indicates that a city has a specific historical or commemorative monument |
| case4_detail_strict | hasSenator | 789 | True | State | Politician | represents the relationship where a state has a senator |
| case4_detail_strict | hasSubsidiary | 85 | True | Company | Subsidiary | represents the relationship where a company maintains a subsidiary organization |
| case4_detail_strict | hasTeam | 524 | True | ProfessionalLeague | SportsClub | represents the relationship where a professional league has a team belonging to a sports club |
| case4_detail_strict | hasVariation | 985 | True | Dessert | Dessert | indicates that a dessert has a variation of another dessert |
| case4_detail_strict | headquarteredIn | 386 | True | University | City | indicates that a university is geographically located within a specific city |
| case4_detail_strict | headquarters | 111 | True | TelevisionNetwork | Headquarters | indicates that a television network has its administrative center in a specific building |
| case4_detail_strict | headquartersLocation | 99 | True | AirlineCompany | City | indicates that an airline company has its headquarters in a city |
| case4_detail_strict | height | 90 | True | Athlete | Height | indicates that an athlete has a specific height measurement |
| case4_detail_strict | heldOfficeWhile | 862 | True | Politician | Politician | indicates that a politician held office during the tenure of another politician |
| case4_detail_strict | homeGround | 88 | True | SportsTeam | Stadium | indicates that a sports team has a designated home ground venue |
| case4_detail_strict | icaoIdentifier | 355 | True | Aerodrome | ICAOIdentifier | indicates that an aerodrome is assigned a unique ICAO identifier |
| case4_detail_strict | icaoLocationIdentifier | 14 | True | Aerodrome | ICAOIdentifier | represents the relationship where an aerodrome is assigned a unique ICAO identifier |
| case4_detail_strict | inOfficeWith | 344 | True | Politician | Politician | indicates that two politicians held office simultaneously |
| case4_detail_strict | industry | 187 | True | Company | BuildingMaterials | represents the relationship where a company operates within a specific industry category |
| case4_detail_strict | ingredient | 147 | True | MexicanDessert | DairyProduct | indicates that a Mexican dessert contains a dairy-based ingredient |
| case4_detail_strict | ingredients | 24 | True | DessertFood | FoodIngredients | indicates that a dessert food is composed of specific ingredients |
| case4_detail_strict | inhabit | 790 | True | Nation | Country | represents the relationship where a nation is inhabited by a specific country |
| case4_detail_strict | inhabitant | 24 | True | GeopoliticalEntity | HumanPopulation | represents the relationship where a country is populated by its inhabitants |
| case4_detail_strict | inhabitants | 67 | True | Country | Population | indicates that a country is inhabited by a population |
| case4_detail_strict | inhabitedBy | 485 | True | Mexico | HumanPopulation | represents the relationship where the inhabitants of Mexico are the Mexicans |
| case4_detail_strict | isA | 19 | True |  |  |  |
| case4_detail_strict | isAffiliatedTo | 133 | True |  |  |  |
| case4_detail_strict | isAffiliatedWith | 198 | True |  |  |  |
| case4_detail_strict | isAnEthnicGroup | 1034 | True |  |  |  |
| case4_detail_strict | isAssociatedWith | 131 | True |  |  |  |
| case4_detail_strict | isBasedAt | 345 | True | BroadcastingCompany | Building | indicates that a broadcasting company operates from a physical workplace |
| case4_detail_strict | isBasedIn | 51 | True | Airport | City | indicates that an airport is geographically located within a city |
| case4_detail_strict | isCapitalOf | 669 | True | Country | Country | represents the relationship where a country is the capital of itself |
| case4_detail_strict | isCategorizedAs | 810 | True | Monument | MonumentClassification | represents the relationship where a monument is classified as a contributing property |
| case4_detail_strict | isCategoryOf | 727 | True |  |  |  |
| case4_detail_strict | isChampion | 82 | True | SportsClub | BooleanValue | indicates that a sports club is the champion of a league |
| case4_detail_strict | isChampionOf | 284 | True | SportsTeam | League | indicates that a sports team won a championship in a league competition |
| case4_detail_strict | isChiefOf | 866 | True | HistoricalFigure | AerospaceAgency | indicates that a historical figure leads an aerospace agency |
| case4_detail_strict | isContributing_Property | 873 | True | HistoricalMonument | TrueValue | represents the relationship where a historical monument is considered significant or contributing to a site |
| case4_detail_strict | isDessert | 791 | True | SweetDish | LogicalValue | represents the relationship where a dessert dish is classified as a dessert |
| case4_detail_strict | isEthnicGroup | 427 | True | Community | Nation | represents the relationship where an ethnic group is part of a national entity |
| case4_detail_strict | isEthnicGroupIn | 882 | True | Ethnicity | Nation | a relation between Ethnicity and Nation |
| case4_detail_strict | isFoundationPlace | 499 | True | FoundationPlace | FoundationPlace | indicates that a FoundationPlace serves as the origin or basis of another FoundationPlace |
| case4_detail_strict | isFrom | 725 | True | Individual | Thing | indicates that an individual is from a specific entity |
| case4_detail_strict | isHomeTo | 466 | True | EducationalBuilding | EducationalInstitution | indicates that an educational building houses an educational institution |
| case4_detail_strict | isLeaderOf | 303 | True | Politician | Thing | indicates that a politician holds leadership over a specific entity |
| case4_detail_strict | isLeagueChampion | 189 | True | SportsTeam | ChampionStatus | indicates that a sports team is the current champion of a league |
| case4_detail_strict | isLocatedAt | 887 | True | Structure | Location | indicates that a constructed facility is physically situated within a geographic location |
| case4_detail_strict | isLocatedIn | 48 | True | HistoricalMonument | Municipality | indicates that a historical monument is located within a populated place |
| case4_detail_strict | isLocationOf | 969 | True | Country | Population | represents the relationship where a country is the location of its population |
| case4_detail_strict | isManagedBy | 367 | True | City | GovernmentPosition | indicates that a city is managed by a specific government position |
| case4_detail_strict | isMemberOf | 152 | True | Politician | PoliticalParty | indicates that a politician belongs to a political party organization |
| case4_detail_strict | isNationalityOf | 669 | True | Country | Individual | indicates that a country is the nationality of an individual |
| case4_detail_strict | isNear | 744 | True | HistoricalMonument | County | indicates that a historical monument is located near another county |
| case4_detail_strict | isPartOf | 1 | True | City | State | indicates that a city is administratively part of a state |
| case4_detail_strict | isServedAs | 305 | True | FoodItem | MealComponent | represents the relationship where a food item is part of a meal course |
| case4_detail_strict | isServedBy | 354 | True | Autodrome | Aerodrome | indicates that an autodrome is served by another location |
| case4_detail_strict | isStarOf | 562 | True | Actor | AnimatedCharacter | indicates that an actor stars in an animated character |
| case4_detail_strict | isType | 1077 | True |  |  |  |
| case4_detail_strict | isWestOf | 836 | True | City | County | indicates that a city is located west of a county |
| case4_detail_strict | jobTitle | 771 | True | MilitaryPerson | MilitaryRole | indicates that a military person holds a specific combat leadership role |
| case4_detail_strict | keyPerson | 461 | True | PharmaceuticalCompany | Executive | represents the relationship where a pharmaceutical company is led by a high-ranking executive |
| case4_detail_strict | keyPersonAt | 1113 | True | KeyPerson | MassMediaCompany | indicates that a key person holds a significant role within a mass media company |
| case4_detail_strict | keyPersonFor | 609 | True | KeyPerson | Company | indicates that a key person oversees a company |
| case4_detail_strict | language | 340 | True | Nation | ModernLanguage | represents the relationship where a nation employs a modern form of a language |
| case4_detail_strict | lastAired | 366 | True | TVSeries | EventDate | indicates that a TV series concludes on a specific event date |
| case4_detail_strict | lastAiredOn | 167 | True | Program | Date | indicates that a program was last aired on a specific date |
| case4_detail_strict | lastProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was last manufactured in a specific year |
| case4_detail_strict | leader | 196 | True | City | Politician | represents the relationship where a city is governed by a political leader |
| case4_detail_strict | leaderName | 251 | True | City | Leader | represents the relationship where a city is led by a specific person |
| case4_detail_strict | leaderTitle | 1 | True | City | LeaderTitle | indicates that a city has a leadership role title |
| case4_detail_strict | leadershipTitle | 280 | True | Country | LeadershipRole | indicates that a country has a specific title for its leadership role |
| case4_detail_strict | league | 16 | True | SportsTeam | League | indicates that a sports team competes in a specific league |
| case4_detail_strict | leagueTitle | 975 | True | SportsTeam | League | indicates that a sports team competes in a specific league title |
| case4_detail_strict | length | 2 | True | Locomotive | Length | represents the relationship where a locomotives physical dimension is defined |
| case4_detail_strict | locatedIn | 643 | True | EducationalInstitution | City | indicates that an educational institution is geographically located within a specific city |
| case4_detail_strict | locatedInAdministrativeTerritory |  | False | Location | AdministrativeTerritory | Indicates that a location is located within a specific administrative territorial entity. |
| case4_detail_strict | locatedInCountry | 17 | True | Location | Country | Indicates that a location is located in a country. |
| case4_detail_strict | location | 0 | True | Company | City | represents the relationship where a companys physical presence is located within a city |
| case4_detail_strict | locationCity | 872 | True | BroadcastingCompany | City | indicates that a broadcasting company is headquartered in a specific city |
| case4_detail_strict | locationElevation | 56 | True | Aerodrome | Elevation | indicates that an aerodrome has a specific elevation above sea level |
| case4_detail_strict | locationInTimezone | 852 | True | City | Zone | indicates that a city is located in a specific time zone |
| case4_detail_strict | locationOf | 528 | True | County | Monument | represents the relationship where a county is the location of a monument |
| case4_detail_strict | locationOfBroadcast | 167 | True | Program | Building | indicates that a program is broadcast from a specific building |
| case4_detail_strict | locationOfDeath | 173 | True | Country | Country | indicates that a country is the location of an individual's death |
| case4_detail_strict | locationOfFounding | 808 | True | Company | City | indicates that a company was founded in a specific city location |
| case4_detail_strict | locationOfOccurrence | 449 | True | Ingredient | Country | indicates that an ingredient is found within a specific country |
| case4_detail_strict | locationOfProduction | 199 | True | Automobile | City | indicates that an automobile was produced in a specific city |
| case4_detail_strict | locationRelation | 78 | True | County | SpatialRelation | represents the relationship where a county is situated relative to another county in a north-south direction |
| case4_detail_strict | longName | 174 | True | Nation | OfficialName | represents the relationship where a nations long name corresponds to its official name |
| case4_detail_strict | mainDishType | 421 | True |  |  |  |
| case4_detail_strict | mainIngredient | 329 | True | Dessert | DairyProduct | indicates that a dessert contains raisins |
| case4_detail_strict | mainOwner | 757 | True | EducationalBuilding | EducationalInstitution | represents the relationship where an educational building is owned by an educational institution |
| case4_detail_strict | mainProduct | 27 | True | Company | Software | represents the relationship where a company specializes in creating software products |
| case4_detail_strict | makes | 22 | True | PharmaceuticalCompany | Medicine | indicates that a pharmaceutical company produces medical products |
| case4_detail_strict | makesProduct | 627 | True | Company | Software | indicates that a company produces software products |
| case4_detail_strict | manager | 5 | True | SportsTeam | Manager | indicates that a sports team is led by a manager |
| case4_detail_strict | managerOfCurrentTeam | 572 | True | Athlete | Manager | indicates that an athlete has a manager for their current team |
| case4_detail_strict | managerTitle | 29 | True | Company | ManagerTitle | indicates that a company is managed by a specific title |
| case4_detail_strict | manages | 192 | True | Athlete | Coach | represents the relationship where an athlete oversees a coaching role |
| case4_detail_strict | manufacturer | 281 | True | Locomotive | Manufacturer | indicates that a locomotive is produced by a specific manufacturer |
| case4_detail_strict | marriage | 640 | True | Individual | Individual | indicates that two individuals are legally or socially united in marriage |
| case4_detail_strict | memberOf | 30 | True | Athlete | YouthTeam | indicates that an athlete is a member of a youth sports team |
| case4_detail_strict | mission | 25 | True | Individual | SpaceMission | indicates that an individual participates in a spaceflight mission |
| case4_detail_strict | monumentCategory | 955 | True |  |  |  |
| case4_detail_strict | monumentLocation | 955 | True | MilitaryUnit | County | represents the relationship where a military units monument is located within a county |
| case4_detail_strict | movedTo | 1161 | True | Company | Country | indicates that a company relocated to a specific country |
| case4_detail_strict | municipality | 7 | True | HistoricalStructure | City | indicates that a historical structure is located within a city |
| case4_detail_strict | name | 479 | True | Stadium | Stadium | indicates that a stadium has a specific name |
| case4_detail_strict | nameOfGround | 659 | True | Stadium | SportsTeam | represents the relationship where a stadium is named after a sports team |
| case4_detail_strict | nationalAnthem | 269 | True | Government | NationalAnthem | represents the relationship where a government holds a national anthem |
| case4_detail_strict | nationality | 11 | True | Individual | Country | indicates that an individual belongs to a specific country |
| case4_detail_strict | nativeOf | 477 | True | State | Bird | indicates that a state is the native home of a bird species |
| case4_detail_strict | nearbyPlace | 966 | True | County | County | indicates that a county has another county nearby |
| case4_detail_strict | neighbor | 403 | True | State | County | indicates that a state shares administrative boundaries with another county |
| case4_detail_strict | netIncome | 149 | True | Company | NetIncome | represents the relationship where a companys net income is a specific financial metric |
| case4_detail_strict | network | 91 | True | TV_series | BroadcastingCompany | indicates that a TV series is broadcasted by a broadcasting company |
| case4_detail_strict | nickname | 88 | True | SportsTeam | Nickname | represents the relationship where a sports team has a distinctive nickname |
| case4_detail_strict | northNeighbour | 165 | True | County | County | indicates that a county is geographically located north of another county |
| case4_detail_strict | northOf | 528 | True | County | County | indicates that one county is geographically situated north of another |
| case4_detail_strict | numberOfDoctoralStudents | 900 | True | University | Number | indicates that a university has a specific number of doctoral students |
| case4_detail_strict | numberOfEmployees | 114 | True | Company | Number | indicates that a company has a specific number of employees |
| case4_detail_strict | numberOfMembers | 5 | True | SportsTeam | Number | indicates that a sports team has a specific number of members |
| case4_detail_strict | numberOfPages | 72 | True | Book | Pages | indicates that a book has a specific number of pages |
| case4_detail_strict | numberOfPostgraduateStudents | 1075 | True | University | PostgraduateStudents | represents the relationship where a university has a specific number of postgraduate students |
| case4_detail_strict | numberOfPostgraduates | 654 | True | EducationalInstitution | StudentCount | indicates that an educational institution has a specific number of postgraduate students |
| case4_detail_strict | numberOfStaffMembers | 448 | True | University | NumberOfStaffMembers | indicates that a university has a specific number of staff members |
| case4_detail_strict | numberOfStudents | 66 | True | University | StudentCount | indicates that a university has a total count of students including various levels and staff members |
| case4_detail_strict | numberOfUndergraduateStudents | 237 | True | University | Number_of_UndergraduateStudents | indicates that a university has a specific count of undergraduate students enrolled |
| case4_detail_strict | occupation | 13 | True | MilitaryPerson | MilitaryOccupation | indicates that a military person holds a specific military role |
| case4_detail_strict | offersServices | 737 | True | Company | WebServices | represents the relationship where a company provides services related to the World Wide Web |
| case4_detail_strict | officeHolder | 28 | True | Politician | Politician | indicates that a politician holds a position equivalent to another politician |
| case4_detail_strict | officialLanguage | 183 | True | State | OfficialLanguage | represents the relationship where a state has a primary official language |
| case4_detail_strict | officialName | 1162 | True | Nation | OfficialName | represents the relationship where a nations official name is its primary identifier |
| case4_detail_strict | operatedBy | 10 | True | Airbase | MilitaryBranch | indicates that an airbase is managed by a military branch |
| case4_detail_strict | operates | 51 | True | Airline | Airport | indicates that an airline manages an airport facility |
| case4_detail_strict | operatingArea | 802 | True | Company | Country | represents the relationship where a company operates within a specific country |
| case4_detail_strict | operatingOrganisation | 180 | True |  |  |  |
| case4_detail_strict | operatingOrganisationFor | 463 | True |  |  |  |
| case4_detail_strict | operatingOrganization | 132 | True | Aerodrome | OperatingOrganization | represents the relationship where an aerodrome is managed by an operating organization |
| case4_detail_strict | operator | 40 | True | Airport | AeronauticsCompany | indicates that an airport is managed by an aeronautics company |
| case4_detail_strict | orbitalPeriod | 33 | True | Asteroid | OrbitalPeriod | indicates that an asteroid has a specific orbital period |
| case4_detail_strict | orbital_period | 256 | True | Asteroid | OrbitalPeriod | indicates that an asteroid takes a specific duration to complete one orbit around the Sun |
| case4_detail_strict | origin | 630 | True | Musician | City | indicates that a musician originates from a specific city |
| case4_detail_strict | originCountry | 108 | True | Musician | Nation | indicates that a musician originates from a sovereign state |
| case4_detail_strict | otherTeam | 395 | True | Athlete | SportsTeam | indicates that an athlete is associated with another sports team |
| case4_detail_strict | ownedBuilding | 588 | True | EducationalInstitution | EducationalBuilding | indicates that an educational institution owns a specific educational building |
| case4_detail_strict | ownedBy | 374 | True | Structure | EducationalInstitution | indicates that a structure is owned by an educational institution |
| case4_detail_strict | owner | 38 | True | EducationalFacility | EducationalInstitution | indicates that an educational institution owns a specific facility |
| case4_detail_strict | owns | 112 | True | University | Structure | indicates that a university institution possesses a specific building structure |
| case4_detail_strict | parent | 111 | True | Actor | Daughter | indicates that an actor has a daughter |
| case4_detail_strict | parentCompany | 609 | True | Company | Company | represents the relationship where a company is the parent entity of another company |
| case4_detail_strict | partOf | 977 | True | Astronaut | SpaceMission | represents the relationship where an astronaut is part of a spaceflight undertaking |
| case4_detail_strict | people | 1093 | True | Region | Nationality | represents the relationship where a region is inhabited by a specific nationality |
| case4_detail_strict | peopleName | 171 | True | Nation | PeopleGroup | represents the relationship where a nation has a specific name for its people |
| case4_detail_strict | periapsis | 49 | True | Asteroid | Periapsis | indicates that an asteroid has a specific periapsis distance |
| case4_detail_strict | placeOfBirth | 141 | True | Individual | BirthPlace | indicates that an individual was born in a specific geographic location |
| case4_detail_strict | placeOfDeath | 154 | True | HistoricalFigure | State | indicates that a historical figure died in a specific state |
| case4_detail_strict | placeOfOrigin | 52 | True | Individual | State | indicates that an individuals place of origin is within a specific state |
| case4_detail_strict | placeOfUpbringing | 722 | True | Individual | Country | indicates that an individual grew up in a sovereign country |
| case4_detail_strict | playInLeague | 319 | True | SportsTeam | ProfessionalLeague | represents the relationship where a sports team is affiliated with a professional sports league |
| case4_detail_strict | playedFor | 95 | True | Athlete | SportsTeam | indicates that an athlete competes for a sports team |
| case4_detail_strict | playedIn | 179 | True | SportsClub | Year | indicates that a sports club participated in a competition in a specific year |
| case4_detail_strict | playedInLeague | 479 | True | SportsTeam | League | represents the relationship where a sports team competes in a league |
| case4_detail_strict | playedInSeason | 76 | True | SportsTeam | Year | indicates that a sports team competes in a specific season |
| case4_detail_strict | playedWith | 20 | True | Musician | Band | indicates that a musician is a member of a band |
| case4_detail_strict | playground | 1101 | True | SportsClub | Stadium | indicates that a sports club has a designated sports facility |
| case4_detail_strict | playsInstrument | 50 | True | Musician | MusicalInstrument | indicates that a musician uses a specific musical instrument in their performances |
| case4_detail_strict | playsMusic | 607 | True | Musician | Genre | indicates that a musician performs music within a specific genre |
| case4_detail_strict | population | 1 | True | City | Population | indicates that a city has a total population count |
| case4_detail_strict | populationDensity | 1 | True | City | PopulationDensity | indicates that a city has a specific population density |
| case4_detail_strict | populationGroup | 58 | True | Nation | EthnicGroup | indicates that a nation is composed of a specific ethnic group |
| case4_detail_strict | populationMetro | 458 | True | MetropolitanArea | Population | indicates that a metropolitan area has a total population count |
| case4_detail_strict | position | 217 | True | Politician | LegislativeOffice | indicates that a politician holds a legislative office position |
| case4_detail_strict | postalCode | 296 | True | Village | PostalCode | represents the relationship where a village is linked to a standardized alphanumeric postal code |
| case4_detail_strict | postalCodeRange | 561 | True | City | PostalCodeRange | represents the relationship where a citys postal codes are grouped within a specific range |
| case4_detail_strict | postgraduateStudents | 193 | True | University | PostgraduateStudentsCount | indicates that a university has a specific number of postgraduate students enrolled |
| case4_detail_strict | postgraduates | 1127 | True | EducationalInstitution | Postgraduates | indicates that an educational institution has a count of students enrolled in postgraduate programs |
| case4_detail_strict | powerType | 2 | True |  |  |  |
| case4_detail_strict | precedes | 100 | True | FantasyWork | FantasyWork | indicates that one work of fiction follows another in a chronological order |
| case4_detail_strict | predecessorWork | 849 | True | Book | Book | indicates that one book came before another in a series |
| case4_detail_strict | president | 691 | True | EducationalInstitution | Individual | indicates that an educational institution is led by an individual holding a leadership position |
| case4_detail_strict | presidentDuringService | 326 | True | Politician | Politician | indicates that a politician served during the presidency of another politician |
| case4_detail_strict | presidentDuringTenure | 311 | True | Politician | Politician | represents the relationship where a politician serves as president during a specific tenure |
| case4_detail_strict | presidentServedUnder | 429 | True | Politician | Politician | represents the relationship where a politician served under a specific president |
| case4_detail_strict | previousChampion | 88 | True | SportsTeam | SportsTeam | indicates that a sports team has previously won a championship |
| case4_detail_strict | previousPosition | 914 | True | HistoricalFigure | ProfessionalRole | indicates that a historical figure held a previous professional role |
| case4_detail_strict | previousRole | 90 | True | Athlete | TeamRole | indicates that an athlete held a specific role in a previous team |
| case4_detail_strict | previousTeam | 90 | True | Athlete | SportsTeam | indicates that an athlete previously played for a different sports team |
| case4_detail_strict | previouslyLedBy | 1097 | True | City | Politician | represents the relationship where a city was previously governed by a political leader |
| case4_detail_strict | produced | 208 | True | AutomotiveCompany | Automobile | indicates that an automotive company manufactures a specific vehicle model |
| case4_detail_strict | produces | 27 | True | Company | Software | indicates that a company manufactures or develops software products |
| case4_detail_strict | product | 187 | True | Company | HeatingVentilationAir Conditioning | indicates that a company produces a specific type of product |
| case4_detail_strict | productionEndYear | 60 | True | Automobile | Year | indicates that an automobile ends production in a specific year |
| case4_detail_strict | productionEnded | 855 | True | Automobile | Thing | represents the relationship where an automobile production ends at a particular point in time |
| case4_detail_strict | productionLocation | 137 | True | Automobile | State | indicates that an automobile is manufactured in a specific state |
| case4_detail_strict | productionPeriod | 281 | True | Locomotive | ProductionPeriod | indicates that a locomotive was manufactured within a specific time frame |
| case4_detail_strict | productionStartYear | 60 | True | Automobile | Year | indicates that an automobile begins production in a specific year |
| case4_detail_strict | publicationDate | 253 | True | FantasyNovel | PublicationDate | represents the relationship where a fantasy novel has a specific release date |
| case4_detail_strict | publisher | 100 | True | FantasyWork | Publisher | indicates that a publisher is responsible for the publication of a work of fiction |
| case4_detail_strict | receivedAward | 53 | True | HistoricalFigure | MilitaryAward | indicates that a historical figure has been awarded a military honor |
| case4_detail_strict | region | 26 | True | Dessert | GeographicArea | indicates that a dessert is associated with a specific geographic region |
| case4_detail_strict | relateto | 7 | True | County | County | indicates that two counties are geographically adjacent to each other |
| case4_detail_strict | relationToOther | 688 | True | Actor | Daughter | represents the relationship where an actor is the father of another person |
| case4_detail_strict | relationTo_Alan_Shepard | 840 | True | EducationalInstitution | Graduation | represents the relationship where an educational institution is associated with an individual completing an educational program |
| case4_detail_strict | releaseDate | 172 | True | Book | ReleaseDate | indicates that a book was released on a specific date |
| case4_detail_strict | represented | 217 | True | Politician | State | indicates that a politician represents a specific state |
| case4_detail_strict | requiresIngredient | 1051 | True | SweetFood | BakedGood | indicates that a dessert requires a specific type of baked good as one of its ingredients |
| case4_detail_strict | retiredOn | 69 | True | HistoricalFigure | Date | indicates that a historical figure retired on a specific date |
| case4_detail_strict | retirementDate | 885 | True | HistoricalFigure | Year | indicates that a historical figure retired in a specific year |
| case4_detail_strict | revenue | 117 | True | Company | Revenue | represents the relationship where a company generates a specific amount of income |
| case4_detail_strict | role | 332 | True | Citizen | Professional | indicates that a citizen holds a specific professional role |
| case4_detail_strict | rotationPeriod | 33 | True | Asteroid | RotationPeriod | indicates that an asteroid has a specific rotation period |
| case4_detail_strict | rotation_period | 103 | True | Planet | Duration | indicates that a planet completes one rotation in a given duration |
| case4_detail_strict | rotationalPeriod | 109 | True | Asteroid | RotationalPeriod | indicates that an asteroid rotates on its axis in a specific amount of time |
| case4_detail_strict | runwayLength | 10 | True | Airbase | RunwayLength | indicates that an airbase has a specific runway length |
| case4_detail_strict | runwayMaterial | 249 | True | Aerodrome | Concrete | represents the relationship where an aerodrome runway is constructed with concrete |
| case4_detail_strict | runwayName | 40 | True | Airport | RunwayName | indicates that an airport has a specific runway name for identification |
| case4_detail_strict | runwaySurface | 122 | True | Aerodrome | Concrete | indicates that an aerodrome has a runway surface made of concrete |
| case4_detail_strict | runwaySurfaceMaterial | 502 | True | Aerodrome | ConstructionMaterial | indicates that an aerodrome has a runway surface made of a specific construction material |
| case4_detail_strict | runwaySurfaceType | 494 | True |  |  |  |
| case4_detail_strict | school | 703 | True | HistoricalFigure | EducationalInstitution | indicates that a historical figure attended an educational institution |
| case4_detail_strict | selectedBy | 11 | True | Individual | GovernmentAgency | indicates that an individual is selected by a governmental agency |
| case4_detail_strict | selectedYear | 337 | True | HistoricalFigure | SelectionYear | indicates that a historical figure was selected in a specific year |
| case4_detail_strict | selectionYear | 11 | True | GovernmentAgency | Year | indicates that a governmental agency selects individuals in a specific year |
| case4_detail_strict | sells | 22 | True | PharmaceuticalCompany | PersonalCareProduct | indicates that a pharmaceutical company offers personal care products |
| case4_detail_strict | sequelTo | 307 | True | Book | Book | indicates that one book follows another in a series |
| case4_detail_strict | servedAs | 19 | True | DessertFood | Dessert | indicates that a dessert food item is specifically prepared as a sweet course at the end of a meal |
| case4_detail_strict | servedAt | 485 | True | SweetDish | DessertCourse | indicates that a sweet dish is served as part of a dessert course |
| case4_detail_strict | servedBy | 1155 | True | Aerodrome | Autodrome | represents the relationship where an aerodrome is managed by an autodrome |
| case4_detail_strict | serves | 56 | True | Aerodrome | Autodrome | indicates that an aerodrome facilitates the use of another facility |
| case4_detail_strict | servesAs | 569 | True | Nation | SweetDish | indicates that a nation is associated with a particular sweet dish |
| case4_detail_strict | serviceBranch | 154 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure served in a specific military branch |
| case4_detail_strict | shownBy | 388 | True | Film | BroadcastingCompany | indicates that a film is broadcasted by a specific broadcasting company |
| case4_detail_strict | southeastNeighbor | 981 | True | County | County | indicates that a county is geographically adjacent to another county to its southeast |
| case4_detail_strict | southeast_of | 104 | True | County | County | indicates that one county is located southeast of another county |
| case4_detail_strict | southwestNeighbour | 165 | True | County | County | indicates that a county is geographically located southwest of another county |
| case4_detail_strict | sportsOffered | 522 | True | EducationalInstitution | RecreationalSport | indicates that an educational institution offers a recreational sport |
| case4_detail_strict | spouse | 28 | True | Politician | Individual | indicates that a politician is married to an individual |
| case4_detail_strict | staffCount | 871 | True | University | StaffCount | indicates that a university has a total number of staff members employed |
| case4_detail_strict | staffMembers | 66 | True | University | StaffMembers | indicates that a university has a specific number of individuals employed by the institution |
| case4_detail_strict | staffSize | 257 | True | University | StaffSize | indicates that a university has a specific number of staff members |
| case4_detail_strict | staffTotal | 768 | True | University | StaffTotal | indicates that a university has a total number of staff members |
| case4_detail_strict | starred | 765 | True | TelevisionSeries | Actor | indicates that a television series featured an actor in its cast |
| case4_detail_strict | starredIn | 472 | True | Actor | Broadcast | represents the relationship where an actor participates in a broadcast program |
| case4_detail_strict | starring | 91 | True | TV_series | Individual | indicates that a TV series features individual actors |
| case4_detail_strict | starringIn | 1133 | True | Actor | TVShow | indicates that an Actor is a key performer in a TVShow |
| case4_detail_strict | startDate | 997 | True | EducationalFacility | TemporalEntity | indicates that an educational facility was constructed on a specific date |
| case4_detail_strict | startDateConstruction | 112 | True | Structure | Year | indicates that construction on a building began on a specific year |
| case4_detail_strict | startDateOfCareer | 523 | True | TranceMusician | Year | indicates that a trance musician begins their career in a specific year |
| case4_detail_strict | startedPerforming | 20 | True | Musician | Date | indicates that a musician began performing at a specific date |
| case4_detail_strict | status | 146 | True | EducationalInstitution | EducationalStatus | indicates that an educational institution is recognized with a specific designation by a regulatory body |
| case4_detail_strict | statusGrantedBy | 406 | True | EducationalInstitution | RegulatoryBody | indicates that an educational institution has been granted a status by a regulatory body |
| case4_detail_strict | studentBody_size | 379 | True | University | StudentBody_size | represents the relationship where a university has a total student body size |
| case4_detail_strict | studentCount_Doctoral | 871 | True | University | StudentCount_Doctoral | indicates that a university has a specific number of doctoral students enrolled |
| case4_detail_strict | studentCount_Postgraduate | 871 | True | University | StudentCount_Postgraduate | indicates that a university has a specific number of postgraduate students enrolled |
| case4_detail_strict | studentCount_Undergraduate | 871 | True | University | StudentCount_Undergraduate | indicates that a university has a specific number of undergraduate students enrolled |
| case4_detail_strict | studentTotal | 768 | True | University | StudentTotal | indicates that a university has a total number of students enrolled |
| case4_detail_strict | studentType | 871 | True |  |  |  |
| case4_detail_strict | studiedAt | 964 | True | Photographer | EducationalInstitution | indicates that a photographer pursued formal education at an applied arts school |
| case4_detail_strict | studiesAt | 36 | True | Person | EducationalInstitution | Indicates that a person studies at an educational institution. |
| case4_detail_strict | succeededBy | 429 | True | Politician | Politician | indicates that one politician succeeded another in a political role |
| case4_detail_strict | successor | 152 | True | Politician | Politician | represents the relationship where one politician succeeds another in a political role |
| case4_detail_strict | support | 610 | True | University | StudentPopulation | indicates that a university institution provides support services to a student body |
| case4_detail_strict | team | 42 | True | Player | Team | indicates that a player competes with a specific team |
| case4_detail_strict | teamLocation | 700 | True | Athlete | Stadium | indicates that an athletes team is based at a specific stadium |
| case4_detail_strict | technicalCampusAffiliation | 685 | True | EducationalInstitution | RegulatoryBody | indicates that an educational institution is affiliated with a regulatory body responsible for technical education |
| case4_detail_strict | technicalCampusStatus | 978 | True | EducationalInstitution | GrantStatus | represents the relationship where an educational institution is granted a specific status by a regulatory body |
| case4_detail_strict | timeZone | 73 | True | City | Timezone | indicates that a city operates within a specific time zone |
| case4_detail_strict | timezone | 61 | True | City | StandardTimezone | indicates that a city operates under a specific time zone |
| case4_detail_strict | toTheSouthEastOf | 107 | True | County | County | indicates that one county is located to the southeast of another county |
| case4_detail_strict | tookPartIn | 151 | True | Astronaut | SpaceMission | represents the relationship where an astronaut engages in a space-related activity |
| case4_detail_strict | totalArea | 802 | True | Country | Area | indicates that a country has a specific total area |
| case4_detail_strict | totalNumberOfStudents | 386 | True | University | TotalNumberOfStudents | indicates that a university has a specific total number of students enrolled |
| case4_detail_strict | totalStudents | 956 | True | University | TotalStudents | indicates that a university has a total number of students enrolled |
| case4_detail_strict | type | 7 | True |  |  |  |
| case4_detail_strict | undergraduatePopulation | 702 | True | University | UndergraduatePopulation | represents the relationship where a university has a specific number of undergraduate students |
| case4_detail_strict | undergraduateStudentCount | 136 | True | University | UndergraduateStudentCount | indicates that a university has a specific count of undergraduate students |
| case4_detail_strict | undergraduateStudents | 336 | True | University | UndergraduateStudents | indicates that a university has a specific number of undergraduate students enrolled |
| case4_detail_strict | undergraduateTotal | 768 | True | University | UndergraduateTotal | indicates that a university has a specific number of undergraduate students |
| case4_detail_strict | undergraduates | 1127 | True | EducationalInstitution | Undergraduates | indicates that an educational institution has a count of students enrolled in undergraduate programs |
| case4_detail_strict | utcOffset | 1 | True | City | UTCOffset | indicates that a city has a UTC offset |
| case4_detail_strict | wasFoundedBy | 221 | True | BroadcastingCompany | FoundingEntity | indicates that a broadcasting company was founded by a specific founding entity |
| case4_detail_strict | wasInOfficeWhile | 728 | True | Individual | Presidency | indicates that an individual held a position during a specific presidency |
| case4_detail_strict | wasMemberOf | 69 | True | HistoricalFigure | SpaceMission | represents the relationship where a historical figure was part of a space mission |
| case4_detail_strict | wasOn | 375 | True | MilitaryPerson | SpaceMission | indicates that a military person participated in a space mission |
| case4_detail_strict | weight | 46 | True | Individual | Weight | indicates that an individuals weight is measured |
| case4_detail_strict | winLeague | 128 | True | SportsTeam | League | indicates that a sports team has won a league |
| case4_detail_strict | winLeagueTitle | 498 | True | SportsTeam | ProfessionalLeague | indicates that a sports team has won a league title |
| case4_detail_strict | winningLeague | 179 | True | SportsClub | League | indicates that a sports club won a league |
| case4_detail_strict | wonLeague | 76 | True | SportsTeam | League | indicates that a sports team has won a league championship |
| case4_detail_strict | wrote | 351 | True | Author | Book | represents the relationship where an author creates a book |
| case4_detail_strict | year | 82 | True | League | Year | indicates that a league takes place in a specific year |
| case4_detail_strict | yearErected | 247 | True | HistoricalMonument | Year | represents the relationship where a monument is associated with a specific year of erection |
| case4_detail_strict | yearInLeague | 128 | True | SportsTeam | Year | indicates that a sports team has been in a league for a specific year |
| case4_detail_strict | yearInPosition | 242 | True | HistoricalFigure | YearInPosition | indicates that a historical figure served in a leadership role for a specific year |
| case4_detail_strict | yearOfBirth | 909 | True | Individual | Year | indicates that an individual was born in a specific year |
| case4_detail_strict | yearOfDeath | 909 | True | Individual | Year | indicates that an individual died in a specific year |
| case4_detail_strict | yearOfGraduation | 557 | True | Historian | Year | indicates that a historian graduated from their educational institution in a specific year |
| case4_detail_strict | youthFootballClub | 1026 | True | Athlete | YouthFootballClub | indicates that an athlete was initially nurtured by a youth football club |
| case4_detail_strict | youthSideOf | 162 | True | Athlete | SportsTeam | indicates that an athlete is part of a youth team of a sports team |
| case4_detail_strict | youthTeam | 675 | True | Athlete | SportsTeam | represents the relationship where an athlete played for a youth team |
| case5_concat | CEO | 465 | True | Company | CEO | indicates that a company is led by a chief executive officer |
| case5_concat | aboveSeaLevel | 925 | True | City | AboveSeaLevel | indicates that a city is located above a certain sea level |
| case5_concat | absoluteMagnitude | 33 | True | Asteroid | AbsoluteMagnitude | indicates that an asteroid has a specific absolute magnitude |
| case5_concat | absolute_magnitude | 447 | True | CelestialBody | AbsoluteMagnitude | represents the relationship where an asteroid has a specific brightness measurement |
| case5_concat | address | 3 | True | ArchitecturalStructure | GeographicLocation | indicates that an architectural structure has a specific physical address |
| case5_concat | adjacentCounty | 185 | True | County | County | represents the relationship where one county is geographically adjacent to another county |
| case5_concat | affiliatedWith | 254 | True | EducationalCouncil | University | indicates that an educational council is associated with a university institution |
| case5_concat | affiliation | 17 | True | Institute | University | indicates that an educational institution is associated with a university for academic purposes |
| case5_concat | airedOn | 124 | True | TVSeries | BroadcastingCompany | indicates that a TV series is broadcasted by a specific broadcasting company |
| case5_concat | airedShowOn | 345 | True | BroadcastingCompany | EventDate | indicates that a broadcasting company aired a show on a specific date |
| case5_concat | altitudeAboveSeaLevel | 15 | True | Airport | Altitude | indicates that an airport is at a specific altitude above sea level |
| case5_concat | annualRevenue | 1157 | True | Company | AnnualRevenue | represents the total revenue generated by a company in a fiscal year |
| case5_concat | anthem | 225 | True | Monarchy | NationalAnthem | represents the relationship where a monarchy has a national anthem |
| case5_concat | apoapsis | 33 | True | Asteroid | Apoapsis | indicates that an asteroid has a specific apoapsis distance |
| case5_concat | architect | 3 | True | ArchitecturalStructure | Architect | indicates that an architectural structure is designed by a professional architect |
| case5_concat | area | 200 | True | Country | Area | represents the relationship where a countrys geographical extent is quantified |
| case5_concat | areaCode | 74 | True | Place | AreaCode | represents the relationship where a place is uniquely identified by a numeric area code |
| case5_concat | assembledIn | 994 | True | Automobile | City | indicates that an automobile is manufactured in a specific city |
| case5_concat | assemblyLineLocation | 39 | True | Vehicle | City | indicates that a vehicle was produced on an assembly line located within a city |
| case5_concat | assemblyLocation | 624 | True | Automobile | City | indicates that an automobile is assembled in a specific city |
| case5_concat | associatedBand | 721 | True | Musician | MusicalGroup | indicates that a musician is associated with a musical group |
| case5_concat | associatedWith | 400 | True | Musician | Musician | indicates that a musician collaborates with another artist in musical projects |
| case5_concat | attendedSchool | 312 | True | Individual | School | indicates that an individual studied at a specific educational institution |
| case5_concat | author | 72 | True | Book | Author | indicates that a book is authored by an individual |
| case5_concat | award | 349 | True | HistoricalFigure | MilitaryAward | indicates that a historical figure was recognized with a military award |
| case5_concat | awarded | 599 | True | HistoricalFigure | Medal | represents the relationship where a historical figure receives a distinguished service medal |
| case5_concat | awardedBy | 349 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure received a military award from a branch of the armed forces |
| case5_concat | awardedTechnicalCampusStatusTo | 131 | True | GovernmentAgency | EducationalInstitution | represents the relationship where a government agency grants a technical campus status to an educational institution |
| case5_concat | awardedTo | 154 | True | MilitaryBranch | HistoricalFigure | indicates that a military branch awards a specific historical figure a medal |
| case5_concat | awardingBody | 615 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure is awarded by a specific military branch |
| case5_concat | becameProfessional | 582 | True | Individual | Profession | indicates that an individual transitioned into a professional role |
| case5_concat | beganCareerIn | 893 | True | Musician | Date | indicates that a musician starts their professional career at a specific date |
| case5_concat | beganMusicalCareer | 400 | True | Musician | Year | represents the relationship where a musician starts their professional music career |
| case5_concat | beganPerforming | 376 | True | Musician | Date | indicates that a musician starts performing at a specific point in time |
| case5_concat | birthDate | 13 | True | MilitaryPerson | Date | indicates that a military person was born on a specific date |
| case5_concat | birthPlace | 28 | True | Politician | City | indicates that a politician was born in a specific city |
| case5_concat | birthYear | 34 | True | HistoricalFigure | Year | indicates that a historical figure was born in a specific year |
| case5_concat | birthplace | 879 | True | Individual | City | represents the relationship where an individuals place of birth is a city |
| case5_concat | bodyStyle | 399 | True | Automobile | BodyStyle | represents the relationship where an automobile has a specific body style |
| case5_concat | borderingCounty | 906 | True | County | County | indicates that a county shares borders with other counties |
| case5_concat | born | 631 | True | MilitaryPerson | BirthDate | indicates that a military person was born on a specific date |
| case5_concat | bornIn | 4 | True | Individual | City | indicates that an individual is born in a specific city |
| case5_concat | bornOn | 30 | True | Athlete | BirthDate | indicates that an athlete was born on a specific date |
| case5_concat | bornWithin | 357 | True | Individual | Monarchy | indicates that an individual was born within a monarchy |
| case5_concat | born_on | 805 | True | Astronaut | BirthDate | indicates that an astronaut was born on a specific date |
| case5_concat | broadcastedBy | 6 | True | TVShow | BroadcastingCompany | indicates that a TV show is broadcast by a specific broadcasting company |
| case5_concat | broughtUpBy | 250 | True | MediaCompany | AnimatedCharacter | represents the relationship where a media company is associated with a specific animated character |
| case5_concat | buildStartDate | 965 | True | EducationalBuilding | TemporalValue | indicates that a building was constructed on a specific date |
| case5_concat | builder | 105 | True | Locomotive | Company | represents the relationship where a locomotive is produced by a manufacturing company |
| case5_concat | builtBetween | 150 | True | Locomotive | HistoricalPeriod | indicates that a locomotive was constructed within a specific historical time frame |
| case5_concat | builtIn | 7 | True | HistoricalStructure | TimePeriod | indicates that a historical structure is constructed in a specific year |
| case5_concat | builtOn | 278 | True | EducationalBuilding | ConstructionDate | indicates that an educational building was constructed on a specific date |
| case5_concat | campusLocation | 410 | True | University | Road | indicates that a university is situated on a specific road within its campus |
| case5_concat | campusStatus | 974 | True | EducationalInstitution | CampusStatus | indicates that an educational institution has been granted a specific status by a governing body |
| case5_concat | campus_location | 563 | True | EducationalInstitution | Address | indicates that an educational institution has a specific campus location |
| case5_concat | canBeVaryWith | 67 | True | Dessert | DairyProduct | indicates that a dessert can be prepared with a dairy product |
| case5_concat | categorization | 501 | True | HistoricalStructure | HistoricResource | indicates that a historical structure is recognized as a resource contributing to the significance of a district |
| case5_concat | category | 104 | True |  |  |  |
| case5_concat | ceremonialCounty | 830 | True | Town | CeremonialCounty | represents the relationship where a town is part of a ceremonial county |
| case5_concat | champion | 568 | True | SoccerLeague | SportsTeam | indicates that a soccer league has a champion sports team |
| case5_concat | championOf | 659 | True | SportsTeam | League | represents the relationship where a sports team is the champion of a league |
| case5_concat | champions | 16 | True | SportsTeam | League | indicates that a sports team is the champion of a league |
| case5_concat | championship | 920 | True | SportsClub | League | indicates that a sports club has won a specific league championship |
| case5_concat | championships | 629 | True | SportsTeam | Number | indicates that a sports team has won a specific number of championships |
| case5_concat | channel | 384 | True | TVSeries | BroadcastingCompany | indicates that a TV series is broadcasted on a specific television channel operated by a broadcasting company |
| case5_concat | character | 688 | True | Actor | TelevisionSeries | indicates that an actor portrays a character in a television series |
| case5_concat | citizens | 369 | True | Nation | Population | represents the relationship where a nation comprises a specific demographic group |
| case5_concat | citizenship | 28 | True | Politician | Nation | indicates that a politician holds citizenship in a specific nation |
| case5_concat | city | 418 | True | EducationalInstitution | City | indicates that an educational institution is located in a specific city |
| case5_concat | cityManager | 913 | True | City | Position | indicates that a city is led by a specific leadership role |
| case5_concat | coach | 295 | True | Team | Coach | represents the relationship where a coach leads a sports team |
| case5_concat | competedIn | 284 | True | SportsTeam | Season | represents the relationship where a sports team participated in a specific season |
| case5_concat | completedOn | 190 | True | ArchitecturalStructure | CompletionDate | indicates that an architectural structure is finished on a specific completion date |
| case5_concat | completionDate | 112 | True | Structure | Year | indicates that a building was completed on a specific year |
| case5_concat | constructionEnd | 588 | True | EducationalBuilding | Date | indicates that an educational building was completed on a specific date |
| case5_concat | constructionPeriod | 47 | True | Structure | Period | indicates that a structure was built within a specific time frame |
| case5_concat | constructionStart | 361 | True | Facility | Temporal | indicates that a facilitys construction began on a specific date |
| case5_concat | constructionStartDate | 1121 | True | EducationalBuilding | ConstructionStartDate | indicates that an educational building has a specific start date for construction |
| case5_concat | contains | 58 | True | SweetDessert | CondensedMilk | indicates that a dessert includes a specific dairy product |
| case5_concat | containsAdministrativeTerritory |  | False | AdministrativeTerritory | AdministrativeTerritory | Indicates that an administrative territory contains another administrative territory. |
| case5_concat | containsIngredient | 986 | True | Dish | Nutrition | indicates that a dish includes granola, shredded coconut, and raisins as nutritional ingredients |
| case5_concat | containsSettlement |  | False | AdministrativeTerritory | Settlement | Indicates that an administrative territory contains a settlement such as a city or town. |
| case5_concat | containsTeam | 284 | True | League | SportsTeam | represents the relationship where a league includes multiple sports teams |
| case5_concat | corporateForm | 29 | True | Company | LegalForm | represents the relationship where a company has a specific legal form |
| case5_concat | cosparId | 416 | True | SpaceMission | CosparId | represents the relationship where a space mission is uniquely identified by a COSPAR ID |
| case5_concat | country | 3 | True | EducationalInstitution | Country | indicates that an educational institution is located in a specific country |
| case5_concat | countryOfBirth | 356 | True | HistoricalFigure | Country | represents the relationship where a historical figure is born in a specific country |
| case5_concat | countryOfCitizenship | 1001 | True | Politician | Nation | indicates that a politician is a citizen of a specific nation |
| case5_concat | countryOfDeath | 689 | True | GeopoliticalEntity | GeopoliticalEntity | indicates that a sovereign state is the place where an individual died |
| case5_concat | countryOfOrigin | 316 | True | Musician | Country | indicates that a musician originates from a specific country |
| case5_concat | countryOrigin | 709 | True | Dessert | Country | indicates that a dessert originates from a specific country |
| case5_concat | county | 7 | True | HistoricalStructure | County | indicates that a historical structure is situated within a county |
| case5_concat | created | 562 | True | Creator | AnimatedCharacter | indicates that a creator produces an animated character |
| case5_concat | creator | 6 | True | TVShow | Creator | represents the relationship where a TV show is created by a specific creator |
| case5_concat | crewMember | 332 | True | SpaceMission | Citizen | indicates that a space mission includes a citizen as a crew member |
| case5_concat | currency | 24 | True | GeopoliticalEntity | MonetaryUnit | indicates that a country uses a specific currency for transactions |
| case5_concat | currentAssemblyLocation | 697 | True | Automobile | City | indicates that an automobile is currently assembled in a specific city |
| case5_concat | currentClub | 30 | True | Athlete | FootballClub | indicates that an athlete is currently affiliated with a football club |
| case5_concat | currentLeader | 699 | True | Nation | Politician | represents the relationship where a nation is led by a political leader |
| case5_concat | currentLocation | 187 | True | Company | Country | indicates that a company is headquartered in a specific country |
| case5_concat | currentPosition | 156 | True | Politician | PoliticalOffice | represents the relationship where a politician holds a current political office position |
| case5_concat | currentSenator | 476 | True | State | Politician | represents the relationship where a state is governed by a current senator |
| case5_concat | currentTeam | 90 | True | Athlete | SportsTeam | indicates that an athlete competes for a specific sports team |
| case5_concat | currentTenants | 3 | True | ArchitecturalStructure | EducationalInstitution | indicates that an architectural structure is currently occupied by an educational institution |
| case5_concat | currentlyPlaysFor | 95 | True | Athlete | SportsTeam | indicates that an athlete is currently affiliated with a sports team |
| case5_concat | dateOfBirth | 25 | True | Individual | BirthDate | indicates that an individual has a specific birth date |
| case5_concat | dateOfDeath | 173 | True | Individual | DeathDate | indicates that an individual died on a specific date |
| case5_concat | dateOfGraduation | 866 | True | HistoricalFigure | AcademicYear | indicates that a historical figure graduated from an academic institution in a specific year |
| case5_concat | dateOfRetirement | 154 | True | HistoricalFigure | RetirementDate | indicates that a historical figure retired on a specific date |
| case5_concat | dateOfRole | 633 | True | HistoricalFigure | HistoricalYear | indicates that a historical figure held a role in a specific year |
| case5_concat | deathCause | 640 | True | Individual | Death | indicates that an individuals death is caused by a natural or medical condition |
| case5_concat | deathDate | 93 | True | Individual | DeathDate | indicates that an individual has a specific death date |
| case5_concat | deathPlace | 69 | True | HistoricalFigure | State | indicates that a historical figure died in a specific state |
| case5_concat | debutTeam | 518 | True | Athlete | Team | indicates that an athlete begins their professional career with a specific team |
| case5_concat | degree | 477 | True | EducationalInstitution | Degree | indicates that an educational institution awarded a specific degree |
| case5_concat | designatedAs | 643 | True | EducationalInstitution | CampusDesignation | represents the relationship where an educational institution is given a specific designation or classification |
| case5_concat | designatedTechnicalCampusStatusTo | 143 | True | Council | Institute | indicates that a council formally recognizes a technical education institution as a campus |
| case5_concat | designed | 887 | True | Professional | Structure | indicates that a professional architect created the design for a constructed facility |
| case5_concat | diedIn | 4 | True | Individual | Country | indicates that an individual dies in a specific country |
| case5_concat | directedBy | 643 | True | EducationalInstitution | EducationalLeader | indicates that an educational institution is led by a person in charge of academic affairs |
| case5_concat | direction | 365 | True | AdministrativeDivision | GeographicalDirection | indicates that a territorial division is geographically positioned relative to another |
| case5_concat | director | 131 | True | EducationalInstitution | Educator | represents the relationship where an educational institution is led by an educator |
| case5_concat | discovered | 182 | True | Astronomer | AstronomicalBody | indicates that an astronomer identifies a celestial body |
| case5_concat | discoveredBy | 33 | True | Asteroid | Astronomer | indicates that an asteroid is identified by an astronomer |
| case5_concat | discoveryDate | 33 | True | Asteroid | Date | indicates that an asteroids discovery is recorded with a specific date |
| case5_concat | doctoralStudentPopulation | 932 | True | University | StudentPopulation | indicates that a university has a specific number of doctoral students |
| case5_concat | doctoralStudents | 66 | True | University | DoctoralStudents | indicates that a university has a specific number of students enrolled in doctoral programs |
| case5_concat | draftPick | 518 | True | Athlete | DraftPick | indicates that an athlete is selected as a draft pick |
| case5_concat | draftPickNumber | 1057 | True | Athlete | DraftPickNumber | indicates that an athlete is assigned a draft pick number |
| case5_concat | earnings | 85 | True | Company | Earnings | indicates that a company generates financial income over a year |
| case5_concat | eat | 790 | True | Dessert | Type | indicates that a dessert is consumed as a type of food |
| case5_concat | educate | 537 | True | University | StudentCount | indicates that a university enrolls a specific number of students |
| case5_concat | educatedAt | 707 | True | FootballClub | Athlete | indicates that a football club has an athlete as a former member |
| case5_concat | educates | 257 | True | University | StudentPopulation | indicates that a university enrolls a total number of students |
| case5_concat | education | 53 | True | HistoricalFigure | Degree | indicates that a historical figure has earned a formal academic degree |
| case5_concat | elevation | 71 | True | Airport | Elevation | indicates that an airport has a specific elevation measurement above sea level |
| case5_concat | elevationAboveSeaLevel | 41 | True | Airport | ElevationAboveSeaLevel | indicates that an airport has a specific elevation above sea level measurement |
| case5_concat | endDateConstruction | 946 | True | Structure | Temporal | indicates that a building was completed at a specific point in time |
| case5_concat | endedManufacturingOf | 325 | True | Automaker | AutomobileModel | indicates that an automaker ceases production of a specific vehicle model |
| case5_concat | engine | 350 | True | Locomotive | Engine | indicates that a locomotive is equipped with a particular type of engine |
| case5_concat | engineType | 65 | True |  |  |  |
| case5_concat | epoch | 64 | True | Asteroid | Time | represents the relationship where an asteroid reaches a specific epoch in its orbit |
| case5_concat | established | 104 | True | HistoricalStructure | Year | indicates that a historical structure was founded in a specific year |
| case5_concat | establishedIn | 146 | True | EducationalInstitution | Year | indicates that an educational institution was founded in a specific year |
| case5_concat | establishmentYear | 138 | True | Monument | Year | indicates that a monument was established in a specific year |
| case5_concat | ethnicGroup | 4 | True | Country | Group | represents the relationship where a country has a specific ethnic group |
| case5_concat | extinctionDate | 558 | True | AutomobileBrand | Year | represents the relationship where an automobile brand ceased operations on a specific year |
| case5_concat | firstAired | 6 | True | TVShow | EventDate | indicates that a TV show marks its premiere on a specific date |
| case5_concat | firstAiredBy | 698 | True | TelevisionShow | BroadcastingCompany | indicates that a television show is broadcasted by a specific broadcasting company |
| case5_concat | firstAiredOn | 21 | True | Program | EventDate | indicates that a program was first broadcasted on a specific date |
| case5_concat | firstAppearance | 260 | True | Film | AnimatedCharacter | represents the relationship where a film features its initial appearance of an animated character |
| case5_concat | firstAppearedAsFilmCharacterIn | 779 | True | FilmCharacter | Film | represents the relationship where a characters first appearance in a film is specified |
| case5_concat | firstBroadcast | 250 | True | AnimatedCharacter | EventDate | indicates that an animated character had its first broadcast on a specific date |
| case5_concat | firstProducedIn | 199 | True | Automobile | Year | indicates that an automobile was first manufactured in a specific year |
| case5_concat | firstProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was first manufactured in a specific year |
| case5_concat | followedBy | 241 | True | Book | Book | indicates that one book series continues another in a narrative sequence |
| case5_concat | formerTeam | 414 | True | Athlete | SportsTeam | indicates that an athlete has previously been associated with a specific sports team |
| case5_concat | formerlyPlayedFor | 782 | True | Athlete | SportsTeam | indicates that an athlete previously played for a sports team |
| case5_concat | formerlyPlayedWith | 318 | True | Athlete | SportsTeam | indicates that an athlete previously played for a sports team |
| case5_concat | foundIn | 19 | True | DessertFood | Country | represents the relationship where a dessert food item is located within a specific country |
| case5_concat | founded | 114 | True | Company | Date | indicates that a company was established on a specific date |
| case5_concat | foundedBy | 120 | True | Company | Founder | represents the relationship where a company is initiated by a person |
| case5_concat | founder | 62 | True | Company | Founder | represents the relationship where a company is initiated and managed by a founder |
| case5_concat | founding | 691 | True | City | HistoricalFigure | represents the relationship where a city is founded by a historical figure |
| case5_concat | foundingDate | 22 | True | PharmaceuticalCompany | FoundingDate | indicates that a pharmaceutical company was established on a specific founding date |
| case5_concat | foundingEntity | 221 | True | BroadcastingCompany | FoundingEntity | represents the relationship where a broadcasting company is established by a founding entity |
| case5_concat | foundingPlace | 114 | True | Company | City | indicates that a company was founded in a specific city |
| case5_concat | foundingYear | 1024 | True | Aerodrome | Year | indicates that an aerodrome was founded in a specific year |
| case5_concat | from | 1060 | True | Musician | City | indicates that a musician is geographically located within a city |
| case5_concat | fullAddress | 392 | True | Institute | Address | indicates that an institute has a specific full physical address |
| case5_concat | fullName | 203 | True | State | Name | indicates that a state has a formal name |
| case5_concat | full_name | 246 | True | SportsTeam | SportsTeam | indicates that a sports team has a formal name |
| case5_concat | gaveStatusBy | 857 | True | EducationalInstitution | EducationalAuthority | indicates that an educational institution is granted a status by an educational authority |
| case5_concat | genre | 91 | True | TV_series | Series | indicates that a TV series belongs to a specific series category |
| case5_concat | governingBody | 748 | True | City | Position | indicates that a city is governed by a specific leadership position |
| case5_concat | governmentForm | 1036 | True | StateFormOfGovernment | UnitaryState | indicates that a state form of government is characterized by a centralized system of governance |
| case5_concat | governmentType | 1 | True |  |  |  |
| case5_concat | governor | 925 | True | City | GovernmentBody | indicates that a city is governed by a government body |
| case5_concat | graduatedFrom | 512 | True | HistoricalFigure | EducationalInstitution | indicates that a historical figure received a degree from an educational institution |
| case5_concat | graduatedIn | 477 | True | HistoricalFigure | Year | indicates that a historical figure graduated in a specific year |
| case5_concat | graduationYear | 242 | True | HistoricalFigure | GraduationYear | indicates that a historical figure completed an educational program in a specific year |
| case5_concat | ground | 16 | True | Stadium | SportsTeam | indicates that a stadium hosts a sports team |
| case5_concat | grounds | 675 | True | SportsTeam | Stadium | indicates that a sports team has a specific ground or stadium |
| case5_concat | hadCampusIn | 492 | True | University | City | indicates that a university had its campus within a specific city |
| case5_concat | has | 48 | True | AdministrativeDivision | AdministrativeDivision | indicates that a territorial division contains another territorial division |
| case5_concat | hasBird | 282 | True | State | Species | represents the relationship where a state is associated with a specific bird species |
| case5_concat | hasCylinderCount | 426 | True | Locomotive | CylinderCount | indicates that a locomotive has a specific number of cylinders |
| case5_concat | hasDessert | 791 | True | City | SweetDish | indicates that a city has a specific dessert dish |
| case5_concat | hasDoctoralStudents | 462 | True | University | DoctoralStudents | indicates that a university enrolls a specific number of doctoral students |
| case5_concat | hasIngredient | 929 | True | Dish | Ingredient | represents the relationship where a dish has a variety of ingredients |
| case5_concat | hasItem | 171 | True | UrbanCenter | SweetFood | represents the relationship where an urban center has another specific type of sweet food item |
| case5_concat | hasMember | 360 | True | Band | Musician | represents the relationship where a band comprises a musician |
| case5_concat | hasNativeBird | 505 | True | State | Bird | represents the relationship where a state is home to a specific native bird species |
| case5_concat | hasOfficial | 493 | True | State | Official | represents the relationship where a state appoints an official to lead its administration |
| case5_concat | hasPart | 727 | True | GeographicArea | GeographicArea | represents the relationship where one geographic area contains another |
| case5_concat | hasPopulationDensity | 669 | True | Country | PopulationDensity | represents the relationship where a country has a specific population density |
| case5_concat | hasProperty | 836 | True | City | Monument | indicates that a city has a specific historical or commemorative monument |
| case5_concat | hasSenator | 789 | True | State | Politician | represents the relationship where a state has a senator |
| case5_concat | hasSubsidiary | 85 | True | Company | Subsidiary | represents the relationship where a company maintains a subsidiary organization |
| case5_concat | hasVariation | 985 | True | Dessert | Dessert | indicates that a dessert has a variation of another dessert |
| case5_concat | headquarteredIn | 386 | True | University | City | indicates that a university is geographically located within a specific city |
| case5_concat | headquarters | 111 | True | TelevisionNetwork | Headquarters | indicates that a television network has its administrative center in a specific building |
| case5_concat | headquartersLocation | 99 | True | AirlineCompany | City | indicates that an airline company has its headquarters in a city |
| case5_concat | height | 90 | True | Athlete | Height | indicates that an athlete has a specific height measurement |
| case5_concat | heldOfficeWhile | 862 | True | Politician | Politician | indicates that a politician held office during the tenure of another politician |
| case5_concat | homeGround | 88 | True | SportsTeam | Stadium | indicates that a sports team has a designated home ground venue |
| case5_concat | icaoIdentifier | 355 | True | Aerodrome | ICAOIdentifier | indicates that an aerodrome is assigned a unique ICAO identifier |
| case5_concat | icaoLocationIdentifier | 14 | True | Aerodrome | ICAOIdentifier | represents the relationship where an aerodrome is assigned a unique ICAO identifier |
| case5_concat | inOfficeWhile | 950 | True | Politician | Politician | represents the relationship where one politician serves while another is in office |
| case5_concat | inOfficeWith | 344 | True | Politician | Politician | indicates that two politicians held office simultaneously |
| case5_concat | industry | 187 | True | Company | BuildingMaterials | represents the relationship where a company operates within a specific industry category |
| case5_concat | industryClassification | 559 | True | EnergyCompany | EnergySector | represents the relationship where an energy company belongs to the energy industry sector |
| case5_concat | ingredient | 147 | True | MexicanDessert | DairyProduct | indicates that a Mexican dessert contains a dairy-based ingredient |
| case5_concat | ingredients | 24 | True | DessertFood | FoodIngredients | indicates that a dessert food is composed of specific ingredients |
| case5_concat | inhabit | 790 | True | Nation | Country | represents the relationship where a nation is inhabited by a specific country |
| case5_concat | inhabitant | 24 | True | GeopoliticalEntity | HumanPopulation | represents the relationship where a country is populated by its inhabitants |
| case5_concat | inhabitedBy | 485 | True | Mexico | HumanPopulation | represents the relationship where the inhabitants of Mexico are the Mexicans |
| case5_concat | inhabits | 853 | True | State | Bird | represents the relationship where a state is home to a specific bird species |
| case5_concat | is | 826 | True | Thing | Thing | represents the relationship where an entity belongs to a specific category |
| case5_concat | isA | 19 | True |  |  |  |
| case5_concat | isAffiliatedTo | 133 | True |  |  |  |
| case5_concat | isAffiliatedWith | 198 | True |  |  |  |
| case5_concat | isAnEthnicGroup | 1034 | True |  |  |  |
| case5_concat | isAssociatedWith | 131 | True |  |  |  |
| case5_concat | isBasedAt | 345 | True | BroadcastingCompany | Building | indicates that a broadcasting company operates from a physical workplace |
| case5_concat | isBasedIn | 51 | True | Airport | City | indicates that an airport is geographically located within a city |
| case5_concat | isCapitalOf | 669 | True | Country | Country | represents the relationship where a country is the capital of itself |
| case5_concat | isCategorizedAs | 810 | True | Monument | MonumentClassification | represents the relationship where a monument is classified as a contributing property |
| case5_concat | isCategory | 836 | True |  |  |  |
| case5_concat | isCategoryOf | 727 | True |  |  |  |
| case5_concat | isChampion | 82 | True | SportsClub | BooleanValue | indicates that a sports club is the champion of a league |
| case5_concat | isChampionOf | 211 | True | SportsClub | League | indicates that a sports club is the winner of a league competition |
| case5_concat | isChiefOf | 866 | True | HistoricalFigure | AerospaceAgency | indicates that a historical figure leads an aerospace agency |
| case5_concat | isContributing_Property | 873 | True | HistoricalMonument | TrueValue | represents the relationship where a historical monument is considered significant or contributing to a site |
| case5_concat | isDessert | 791 | True | SweetDish | LogicalValue | represents the relationship where a dessert dish is classified as a dessert |
| case5_concat | isEthnicGroup | 437 | True | Community | Nation | indicates that an ethnic group belongs to a sovereign nation |
| case5_concat | isFoundationPlace | 499 | True | FoundationPlace | FoundationPlace | indicates that a FoundationPlace serves as the origin or basis of another FoundationPlace |
| case5_concat | isFrom | 929 | True | Dish | Country | indicates that a dish originates from a specific geographic area |
| case5_concat | isHomeTo | 569 | True | Nation | Citizen | indicates that a nation is the home of a specific group of citizens |
| case5_concat | isLeaderIn | 1160 | True | Politician | Nation | indicates that a politician leads a nation |
| case5_concat | isLeaderOf | 303 | True | Politician | Thing | indicates that a politician holds leadership over a specific entity |
| case5_concat | isLeagueChampion | 189 | True | SportsTeam | ChampionStatus | indicates that a sports team is the current champion of a league |
| case5_concat | isLocatedAt | 887 | True | Structure | Location | indicates that a constructed facility is physically situated within a geographic location |
| case5_concat | isLocatedIn | 48 | True | HistoricalMonument | Municipality | indicates that a historical monument is located within a populated place |
| case5_concat | isLocationOf | 969 | True | Country | Population | represents the relationship where a country is the location of its population |
| case5_concat | isManagedBy | 367 | True | City | GovernmentPosition | indicates that a city is managed by a specific government position |
| case5_concat | isMemberOf | 152 | True | Politician | PoliticalParty | indicates that a politician belongs to a political party organization |
| case5_concat | isNationalityOf | 669 | True | Country | Individual | indicates that a country is the nationality of an individual |
| case5_concat | isNear | 744 | True | HistoricalMonument | County | indicates that a historical monument is located near another county |
| case5_concat | isPartOf | 7 | True | County | State | indicates that a county is a part of a larger state administrative area |
| case5_concat | isServedAs | 305 | True | FoodItem | MealComponent | represents the relationship where a food item is part of a meal course |
| case5_concat | isServedBy | 354 | True | Autodrome | Aerodrome | indicates that an autodrome is served by another location |
| case5_concat | isStarOf | 562 | True | Actor | AnimatedCharacter | indicates that an actor stars in an animated character |
| case5_concat | isType | 1077 | True |  |  |  |
| case5_concat | isWestOf | 836 | True | City | County | indicates that a city is located west of a county |
| case5_concat | jobTitle | 771 | True | MilitaryPerson | MilitaryRole | indicates that a military person holds a specific combat leadership role |
| case5_concat | keyPerson | 461 | True | PharmaceuticalCompany | Executive | represents the relationship where a pharmaceutical company is led by a high-ranking executive |
| case5_concat | keyPersonAt | 1048 | True | KeyPerson | Company | indicates that a key person holds a significant role within a company organization |
| case5_concat | keyPersonFor | 609 | True | KeyPerson | Company | indicates that a key person oversees a company |
| case5_concat | keyPersonIn | 818 | True | KeyPerson | Company | indicates that a key person holds a significant role within a company organization |
| case5_concat | language | 340 | True | Nation | ModernLanguage | represents the relationship where a nation employs a modern form of a language |
| case5_concat | lastAired | 472 | True | Broadcast | EventDate | indicates that a broadcast program concludes on a specific event date |
| case5_concat | lastAiredOn | 167 | True | Program | Date | indicates that a program was last aired on a specific date |
| case5_concat | lastProducedIn | 199 | True | Automobile | Year | indicates that an automobile was last manufactured in a specific year |
| case5_concat | lastProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was last manufactured in a specific year |
| case5_concat | leader | 196 | True | City | Politician | represents the relationship where a city is governed by a political leader |
| case5_concat | leaderName | 251 | True | City | Leader | represents the relationship where a city is led by a specific person |
| case5_concat | leaderTitle | 1 | True | City | LeaderTitle | indicates that a city has a leadership role title |
| case5_concat | leadershipTitle | 280 | True | Country | LeadershipRole | indicates that a country has a specific title for its leadership role |
| case5_concat | league | 16 | True | SportsTeam | League | indicates that a sports team competes in a specific league |
| case5_concat | leagueTitle | 988 | True | SportsClub | LeagueTitle | indicates that a sports club holds a specific title in a competitive sporting event |
| case5_concat | length | 2 | True | Locomotive | Length | represents the relationship where a locomotives physical dimension is defined |
| case5_concat | locatedAt | 643 | True | EducationalInstitution | Address | represents the specific address or location of an educational institution |
| case5_concat | locatedIn | 614 | True | Dessert | Location | indicates that a dessert is served in a specific geographical location |
| case5_concat | locatedInAdministrativeTerritory |  | False | Location | AdministrativeTerritory | Indicates that a location is located within a specific administrative territorial entity. |
| case5_concat | locatedInCountry | 1 | True | Location | Country | Indicates that a location is located in a country. |
| case5_concat | location | 0 | True | Company | City | represents the relationship where a companys physical presence is located within a city |
| case5_concat | locationCity | 872 | True | BroadcastingCompany | City | indicates that a broadcasting company is headquartered in a specific city |
| case5_concat | locationElevation | 56 | True | Aerodrome | Elevation | indicates that an aerodrome has a specific elevation above sea level |
| case5_concat | locationInTimezone | 852 | True | City | Zone | indicates that a city is located in a specific time zone |
| case5_concat | locationOf | 498 | True | Stadium | SportsTeam | indicates that a stadium is the home ground of a sports team |
| case5_concat | locationOfBroadcast | 167 | True | Program | Building | indicates that a program is broadcast from a specific building |
| case5_concat | locationOfFounding | 808 | True | Company | City | indicates that a company was founded in a specific city location |
| case5_concat | locationOfManufacture | 580 | True | Automobile | City | indicates that an automobile is manufactured in a specific city |
| case5_concat | locationOfOccurrence | 449 | True | Ingredient | Country | indicates that an ingredient is found within a specific country |
| case5_concat | locationOfProduction | 199 | True | Automobile | City | indicates that an automobile was produced in a specific city |
| case5_concat | locationRelation | 78 | True | County | SpatialRelation | represents the relationship where a county is situated relative to another county in a north-south direction |
| case5_concat | longName | 174 | True | Nation | OfficialName | represents the relationship where a nations long name corresponds to its official name |
| case5_concat | magnitude | 739 | True | Asteroid | Magnitude | indicates that an asteroid has a numerical measure of its brightness |
| case5_concat | mainDishType | 421 | True |  |  |  |
| case5_concat | mainIngredient | 329 | True | Dessert | DairyProduct | indicates that a dessert contains raisins |
| case5_concat | mainProduct | 27 | True | Company | Software | represents the relationship where a company specializes in creating software products |
| case5_concat | makes | 22 | True | PharmaceuticalCompany | Medicine | indicates that a pharmaceutical company produces medical products |
| case5_concat | makesProduct | 627 | True | Company | Software | indicates that a company produces software products |
| case5_concat | manager | 5 | True | SportsTeam | Manager | indicates that a sports team is led by a manager |
| case5_concat | managerOfCurrentTeam | 572 | True | Athlete | Manager | indicates that an athlete has a manager for their current team |
| case5_concat | managerTitle | 29 | True | Company | ManagerTitle | indicates that a company is managed by a specific title |
| case5_concat | manages | 192 | True | Athlete | Coach | represents the relationship where an athlete oversees a coaching role |
| case5_concat | manufacturingEndDate | 325 | True | AutomobileModel | ManufacturingEndDate | represents the relationship where a specific vehicle model has a defined end date for production |
| case5_concat | marriage | 640 | True | Individual | Individual | indicates that two individuals are legally or socially united in marriage |
| case5_concat | memberOf | 30 | True | Athlete | YouthTeam | indicates that an athlete is a member of a youth sports team |
| case5_concat | mission | 25 | True | Individual | SpaceMission | indicates that an individual participates in a spaceflight mission |
| case5_concat | monumentCategory | 955 | True |  |  |  |
| case5_concat | monumentLocation | 955 | True | MilitaryUnit | County | represents the relationship where a military units monument is located within a county |
| case5_concat | movedTo | 1161 | True | Company | Country | indicates that a company relocated to a specific country |
| case5_concat | municipality | 7 | True | HistoricalStructure | City | indicates that a historical structure is located within a city |
| case5_concat | name | 479 | True | Stadium | Stadium | indicates that a stadium has a specific name |
| case5_concat | nationalAnthem | 269 | True | Government | NationalAnthem | represents the relationship where a government holds a national anthem |
| case5_concat | nationality | 11 | True | Individual | Country | indicates that an individual belongs to a specific country |
| case5_concat | nativeOf | 477 | True | State | Bird | indicates that a state is the native home of a bird species |
| case5_concat | nearbyPlace | 966 | True | County | County | indicates that a county has another county nearby |
| case5_concat | neighbor | 403 | True | State | County | indicates that a state shares administrative boundaries with another county |
| case5_concat | netIncome | 149 | True | Company | NetIncome | represents the relationship where a companys net income is a specific financial metric |
| case5_concat | network | 91 | True | TV_series | BroadcastingCompany | indicates that a TV series is broadcasted by a broadcasting company |
| case5_concat | nickname | 88 | True | SportsTeam | Nickname | represents the relationship where a sports team has a distinctive nickname |
| case5_concat | northNeighbour | 165 | True | County | County | indicates that a county is geographically located north of another county |
| case5_concat | northOf | 528 | True | County | County | indicates that one county is geographically situated north of another |
| case5_concat | numberOfAcademicStaff | 556 | True | EducationalInstitution | Number | indicates that an educational institution employs a specific number of academic staff |
| case5_concat | numberOfDoctoralStudents | 237 | True | University | Number_of_DoctoralStudents | indicates that a university has a specific count of doctoral students enrolled |
| case5_concat | numberOfEmployees | 114 | True | Company | Number | indicates that a company has a specific number of employees |
| case5_concat | numberOfMembers | 5 | True | SportsTeam | Number | indicates that a sports team has a specific number of members |
| case5_concat | numberOfPages | 72 | True | Book | Pages | indicates that a book has a specific number of pages |
| case5_concat | numberOfPostgraduates | 654 | True | EducationalInstitution | StudentCount | indicates that an educational institution has a specific number of postgraduate students |
| case5_concat | numberOfStaff | 900 | True | University | Number | indicates that a university employs a specific number of staff members |
| case5_concat | numberOfStaffMembers | 448 | True | University | NumberOfStaffMembers | indicates that a university has a specific number of staff members |
| case5_concat | numberOfStudents | 66 | True | University | StudentCount | indicates that a university has a total count of students including various levels and staff members |
| case5_concat | numberOfUndergraduateStudents | 118 | True | University | Number | indicates that a university has a specific count of undergraduate students |
| case5_concat | numberOfUndergraduates | 654 | True | EducationalInstitution | StudentCount | indicates that an educational institution has a specific number of undergraduate students |
| case5_concat | occupation | 13 | True | MilitaryPerson | MilitaryOccupation | indicates that a military person holds a specific military role |
| case5_concat | offersServices | 737 | True | Company | WebServices | represents the relationship where a company provides services related to the World Wide Web |
| case5_concat | offersSport | 643 | True | EducationalInstitution | Activity | indicates that an educational institution provides a specific sport as part of its curriculum or extracurricular activities |
| case5_concat | officeHolder | 28 | True | Politician | Politician | indicates that a politician holds a position equivalent to another politician |
| case5_concat | officeStartDate | 885 | True | HistoricalFigure | Year | indicates that a historical figure began holding an administrative role in a specific year |
| case5_concat | officialLanguage | 183 | True | State | OfficialLanguage | represents the relationship where a state has a primary official language |
| case5_concat | officialName | 1162 | True | Nation | OfficialName | represents the relationship where a nations official name is its primary identifier |
| case5_concat | operatedBy | 10 | True | Airbase | MilitaryBranch | indicates that an airbase is managed by a military branch |
| case5_concat | operates | 51 | True | Airline | Airport | indicates that an airline manages an airport facility |
| case5_concat | operatingArea | 802 | True | Company | Country | represents the relationship where a company operates within a specific country |
| case5_concat | operatingOrganisation | 180 | True |  |  |  |
| case5_concat | operatingOrganisationFor | 463 | True |  |  |  |
| case5_concat | operatingOrganization | 132 | True | Aerodrome | OperatingOrganization | represents the relationship where an aerodrome is managed by an operating organization |
| case5_concat | operator | 40 | True | Airport | AeronauticsCompany | indicates that an airport is managed by an aeronautics company |
| case5_concat | orbitalPeriod | 33 | True | Asteroid | OrbitalPeriod | indicates that an asteroid has a specific orbital period |
| case5_concat | orbital_period | 420 | True | Asteroid | OrbitalPeriod | represents the relationship where an asteroid completes one orbit in a specific period of time |
| case5_concat | origin | 630 | True | Musician | City | indicates that a musician originates from a specific city |
| case5_concat | originCountry | 108 | True | Musician | Nation | indicates that a musician originates from a sovereign state |
| case5_concat | otherTeam | 395 | True | Athlete | SportsTeam | indicates that an athlete is associated with another sports team |
| case5_concat | owner | 228 | True | Structure | Institution | indicates that a building is owned by an educational or administrative body |
| case5_concat | owns | 9 | True | EducationalInstitution | EducationalFacility | indicates that an educational institution possesses a specific educational facility |
| case5_concat | parent | 111 | True | Actor | Daughter | indicates that an actor has a daughter |
| case5_concat | parentCompany | 609 | True | Company | Company | represents the relationship where a company is the parent entity of another company |
| case5_concat | partOf | 977 | True | Astronaut | SpaceMission | represents the relationship where an astronaut is part of a spaceflight undertaking |
| case5_concat | participatedIn | 220 | True | Fighter_pilot | SpaceMission | represents the relationship where a fighter pilot participates in a space mission |
| case5_concat | people | 1093 | True | Region | Nationality | represents the relationship where a region is inhabited by a specific nationality |
| case5_concat | periapsis | 49 | True | Asteroid | Periapsis | indicates that an asteroid has a specific periapsis distance |
| case5_concat | placeOfBirth | 141 | True | Individual | BirthPlace | indicates that an individual was born in a specific geographic location |
| case5_concat | placeOfDeath | 154 | True | HistoricalFigure | State | indicates that a historical figure died in a specific state |
| case5_concat | placeOfOrigin | 52 | True | Individual | State | indicates that an individuals place of origin is within a specific state |
| case5_concat | placeOfUpbringing | 722 | True | Individual | Country | indicates that an individual grew up in a sovereign country |
| case5_concat | playIn | 293 | True | SportsTeam | League | indicates that a sports team competes in a league organized by a governing body |
| case5_concat | playInLeague | 319 | True | SportsTeam | ProfessionalLeague | represents the relationship where a sports team is affiliated with a professional sports league |
| case5_concat | playedFor | 95 | True | Athlete | SportsTeam | indicates that an athlete competes for a sports team |
| case5_concat | playedIn | 179 | True | SportsClub | Year | indicates that a sports club participated in a competition in a specific year |
| case5_concat | playedInLeague | 479 | True | SportsTeam | League | represents the relationship where a sports team competes in a league |
| case5_concat | playedInSeason | 76 | True | SportsTeam | Year | indicates that a sports team competes in a specific season |
| case5_concat | playedWith | 20 | True | Musician | Band | indicates that a musician is a member of a band |
| case5_concat | playground | 1101 | True | SportsClub | Stadium | indicates that a sports club has a designated sports facility |
| case5_concat | playsIn | 566 | True | SportsTeam | ProfessionalLeague | indicates that a sports team competes in a professional league |
| case5_concat | playsInstrument | 50 | True | Musician | MusicalInstrument | indicates that a musician uses a specific musical instrument in their performances |
| case5_concat | playsMusic | 607 | True | Musician | Genre | indicates that a musician performs music within a specific genre |
| case5_concat | population | 1 | True | City | Population | indicates that a city has a total population count |
| case5_concat | populationDensity | 1 | True | City | PopulationDensity | indicates that a city has a specific population density |
| case5_concat | populationMetro | 401 | True | City | Population | indicates that a city has a total metropolitan population count |
| case5_concat | populationTotal | 273 | True | DemographicEntity | Population | represents the relationship where a countrys total population is specified |
| case5_concat | position | 242 | True | HistoricalFigure | MilitaryOrCivilianPosition | indicates that a historical figure held a leadership role within an organization |
| case5_concat | postalCode | 296 | True | Village | PostalCode | represents the relationship where a village is linked to a standardized alphanumeric postal code |
| case5_concat | postalCodeRange | 561 | True | City | PostalCodeRange | represents the relationship where a citys postal codes are grouped within a specific range |
| case5_concat | postgraduateStudents | 66 | True | University | PostgraduateStudents | indicates that a university has a specific number of students enrolled in postgraduate programs |
| case5_concat | powerType | 2 | True |  |  |  |
| case5_concat | precedes | 100 | True | FantasyWork | FantasyWork | indicates that one work of fiction follows another in a chronological order |
| case5_concat | predecessorWork | 849 | True | Book | Book | indicates that one book came before another in a series |
| case5_concat | president | 691 | True | EducationalInstitution | Individual | indicates that an educational institution is led by an individual holding a leadership position |
| case5_concat | presidentDuringService | 326 | True | Politician | Politician | indicates that a politician served during the presidency of another politician |
| case5_concat | presidentDuringTenure | 311 | True | Politician | Politician | represents the relationship where a politician serves as president during a specific tenure |
| case5_concat | presidentServedUnder | 429 | True | Politician | Politician | represents the relationship where a politician served under a specific president |
| case5_concat | previousChampion | 88 | True | SportsTeam | SportsTeam | indicates that a sports team has previously won a championship |
| case5_concat | previousChampions | 419 | True | League | SportsClub | represents the relationship where a league has previously been won by a sports club |
| case5_concat | previousPosition | 914 | True | HistoricalFigure | ProfessionalRole | indicates that a historical figure held a previous professional role |
| case5_concat | previousRole | 90 | True | Athlete | TeamRole | indicates that an athlete held a specific role in a previous team |
| case5_concat | previousTeam | 90 | True | Athlete | SportsTeam | indicates that an athlete previously played for a different sports team |
| case5_concat | previouslyLedBy | 1097 | True | City | Politician | represents the relationship where a city was previously governed by a political leader |
| case5_concat | produced | 208 | True | AutomotiveCompany | Automobile | indicates that an automotive company manufactures a specific vehicle model |
| case5_concat | produces | 27 | True | Company | Software | indicates that a company manufactures or develops software products |
| case5_concat | product | 187 | True | Company | HeatingVentilationAir Conditioning | indicates that a company produces a specific type of product |
| case5_concat | productionEndYear | 60 | True | Automobile | Year | indicates that an automobile ends production in a specific year |
| case5_concat | productionEnded | 855 | True | Automobile | Thing | represents the relationship where an automobile production ends at a particular point in time |
| case5_concat | productionLocation | 137 | True | Automobile | State | indicates that an automobile is manufactured in a specific state |
| case5_concat | productionPeriod | 281 | True | Locomotive | ProductionPeriod | indicates that a locomotive was manufactured within a specific time frame |
| case5_concat | productionStartYear | 60 | True | Automobile | Year | indicates that an automobile begins production in a specific year |
| case5_concat | propertyOf | 244 | True | ArchitecturalStructure | University | indicates that a university owns the architectural structure |
| case5_concat | publicationDate | 253 | True | FantasyNovel | PublicationDate | represents the relationship where a fantasy novel has a specific release date |
| case5_concat | published | 253 | True | Publisher | FantasyNovel | indicates that a publisher releases a fantasy novel into the market |
| case5_concat | publisher | 100 | True | FantasyWork | Publisher | indicates that a publisher is responsible for the publication of a work of fiction |
| case5_concat | receivedAward | 53 | True | HistoricalFigure | MilitaryAward | indicates that a historical figure has been awarded a military honor |
| case5_concat | region | 26 | True | Dessert | GeographicArea | indicates that a dessert is associated with a specific geographic region |
| case5_concat | relateto | 7 | True | County | County | indicates that two counties are geographically adjacent to each other |
| case5_concat | relationToOther | 688 | True | Actor | Daughter | represents the relationship where an actor is the father of another person |
| case5_concat | relationTo_Alan_Shepard | 840 | True | EducationalInstitution | Graduation | represents the relationship where an educational institution is associated with an individual completing an educational program |
| case5_concat | relativePositionTo | 555 | True | County | County | indicates that one county is geographically positioned relative to another county |
| case5_concat | releaseDate | 172 | True | Book | ReleaseDate | indicates that a book was released on a specific date |
| case5_concat | represented | 217 | True | Politician | State | indicates that a politician represents a specific state |
| case5_concat | requires | 860 | True | SweetDish | FoodItem | indicates that a dessert requires a specific food item as an ingredient |
| case5_concat | retiredOn | 69 | True | HistoricalFigure | Date | indicates that a historical figure retired on a specific date |
| case5_concat | retirementDate | 885 | True | HistoricalFigure | Year | indicates that a historical figure retired in a specific year |
| case5_concat | revenue | 117 | True | Company | Revenue | represents the relationship where a company generates a specific amount of income |
| case5_concat | role | 332 | True | Citizen | Professional | indicates that a citizen holds a specific professional role |
| case5_concat | rotationPeriod | 33 | True | Asteroid | RotationPeriod | indicates that an asteroid has a specific rotation period |
| case5_concat | rotation_period | 103 | True | Planet | Duration | indicates that a planet completes one rotation in a given duration |
| case5_concat | rotationalPeriod | 109 | True | Asteroid | RotationalPeriod | indicates that an asteroid rotates on its axis in a specific amount of time |
| case5_concat | runwayLength | 10 | True | Airbase | RunwayLength | indicates that an airbase has a specific runway length |
| case5_concat | runwayMaterial | 249 | True | Aerodrome | Concrete | represents the relationship where an aerodrome runway is constructed with concrete |
| case5_concat | runwayName | 45 | True | Airport | RunwayName | indicates that an airport has a unique runway name |
| case5_concat | runwaySurface | 122 | True | Aerodrome | Concrete | indicates that an aerodrome has a runway surface made of concrete |
| case5_concat | runwaySurfaceMaterial | 502 | True | Aerodrome | ConstructionMaterial | indicates that an aerodrome has a runway surface made of a specific construction material |
| case5_concat | runwaySurfaceType | 494 | True |  |  |  |
| case5_concat | school | 703 | True | HistoricalFigure | EducationalInstitution | indicates that a historical figure attended an educational institution |
| case5_concat | selectedBy | 11 | True | Individual | GovernmentAgency | indicates that an individual is selected by a governmental agency |
| case5_concat | selectionYear | 11 | True | GovernmentAgency | Year | indicates that a governmental agency selects individuals in a specific year |
| case5_concat | sells | 22 | True | PharmaceuticalCompany | PersonalCareProduct | indicates that a pharmaceutical company offers personal care products |
| case5_concat | servedAs | 19 | True | DessertFood | Dessert | indicates that a dessert food item is specifically prepared as a sweet course at the end of a meal |
| case5_concat | servedAt | 485 | True | SweetDish | DessertCourse | indicates that a sweet dish is served as part of a dessert course |
| case5_concat | servedBy | 1155 | True | Aerodrome | Autodrome | represents the relationship where an aerodrome is managed by an autodrome |
| case5_concat | serves | 56 | True | Aerodrome | Autodrome | indicates that an aerodrome facilitates the use of another facility |
| case5_concat | servesAs | 569 | True | Nation | SweetDish | indicates that a nation is associated with a particular sweet dish |
| case5_concat | southeastNeighbour | 165 | True | County | County | indicates that a county is geographically located southeast of another county |
| case5_concat | southeastOf | 1116 | True | County | County | indicates that one county is geographically located to the southeast of another county |
| case5_concat | southeast_of | 104 | True | County | County | indicates that one county is located southeast of another county |
| case5_concat | southwestNeighbour | 165 | True | County | County | indicates that a county is geographically located southwest of another county |
| case5_concat | sportsOffered | 522 | True | EducationalInstitution | RecreationalSport | indicates that an educational institution offers a recreational sport |
| case5_concat | spouse | 28 | True | Politician | Individual | indicates that a politician is married to an individual |
| case5_concat | staffCount | 871 | True | University | StaffCount | indicates that a university has a total number of staff members employed |
| case5_concat | staffMembers | 66 | True | University | StaffMembers | indicates that a university has a specific number of individuals employed by the institution |
| case5_concat | staffSize | 257 | True | University | StaffSize | indicates that a university has a specific number of staff members |
| case5_concat | starred | 167 | True | Program | Actor | indicates that a program features a specific actor |
| case5_concat | starredIn | 472 | True | Actor | Broadcast | represents the relationship where an actor participates in a broadcast program |
| case5_concat | starring | 91 | True | TV_series | Individual | indicates that a TV series features individual actors |
| case5_concat | startDateConstruction | 112 | True | Structure | Year | indicates that construction on a building began on a specific year |
| case5_concat | startedConstructionOn | 374 | True | Structure | YearMonthDay | indicates that a structure began construction on a specific date |
| case5_concat | startedPerforming | 20 | True | Musician | Date | indicates that a musician began performing at a specific date |
| case5_concat | state | 548 | True | AdministrativeDivision | AdministrativeDivision | represents the relationship where an administrative division belongs to a state |
| case5_concat | stateOfDeath | 533 | True | Politician | State | indicates that a politician died in a specific state |
| case5_concat | status | 254 | True | EducationalInstitution | TechnicalCampusStatus | indicates that an educational institution is awarded a technical campus status |
| case5_concat | statusGrantedBy | 406 | True | EducationalInstitution | RegulatoryBody | indicates that an educational institution has been granted a status by a regulatory body |
| case5_concat | studentBody_size | 379 | True | University | StudentBody_size | represents the relationship where a university has a total student body size |
| case5_concat | studentCount_Doctoral | 871 | True | University | StudentCount_Doctoral | indicates that a university has a specific number of doctoral students enrolled |
| case5_concat | studentCount_Postgraduate | 871 | True | University | StudentCount_Postgraduate | indicates that a university has a specific number of postgraduate students enrolled |
| case5_concat | studentCount_Undergraduate | 871 | True | University | StudentCount_Undergraduate | indicates that a university has a specific number of undergraduate students enrolled |
| case5_concat | studentType | 871 | True |  |  |  |
| case5_concat | students | 310 | True | University | StudentCount | indicates that a university has a total number of students |
| case5_concat | studiesAt | 36 | True | Person | EducationalInstitution | Indicates that a person studies at an educational institution. |
| case5_concat | succeededBy | 429 | True | Politician | Politician | indicates that one politician succeeded another in a political role |
| case5_concat | successor | 152 | True | Politician | Politician | represents the relationship where one politician succeeds another in a political role |
| case5_concat | support | 610 | True | University | StudentPopulation | indicates that a university institution provides support services to a student body |
| case5_concat | team | 42 | True | Player | Team | indicates that a player competes with a specific team |
| case5_concat | teamLocation | 700 | True | Athlete | Stadium | indicates that an athletes team is based at a specific stadium |
| case5_concat | technicalCampusAffiliation | 685 | True | EducationalInstitution | RegulatoryBody | indicates that an educational institution is affiliated with a regulatory body responsible for technical education |
| case5_concat | technicalCampusStatus | 978 | True | EducationalInstitution | GrantStatus | represents the relationship where an educational institution is granted a specific status by a regulatory body |
| case5_concat | timeZone | 73 | True | City | Timezone | indicates that a city operates within a specific time zone |
| case5_concat | timezone | 61 | True | City | StandardTimezone | indicates that a city operates under a specific time zone |
| case5_concat | toTheSouthEastOf | 107 | True | County | County | indicates that one county is located to the southeast of another county |
| case5_concat | tookPartIn | 151 | True | Astronaut | SpaceMission | represents the relationship where an astronaut engages in a space-related activity |
| case5_concat | totalArea | 802 | True | Country | Area | indicates that a country has a specific total area |
| case5_concat | totalNumberOfStudents | 136 | True | University | TotalNumberOfStudents | indicates that a university has a comprehensive student body count |
| case5_concat | totalStudents | 352 | True | University | TotalStudents | indicates that a university has a total number of enrolled students |
| case5_concat | type | 7 | True |  |  |  |
| case5_concat | undergraduatePopulation | 702 | True | University | UndergraduatePopulation | represents the relationship where a university has a specific number of undergraduate students |
| case5_concat | undergraduateStudents | 193 | True | University | UndergraduateStudentsCount | indicates that a university has a specific number of undergraduate students enrolled |
| case5_concat | uses | 313 | True | DessertFood | Cheese | indicates that a dessert food item utilizes a specific ingredient |
| case5_concat | utcOffset | 1 | True | City | UTCOffset | indicates that a city has a UTC offset |
| case5_concat | wasFoundedBy | 221 | True | BroadcastingCompany | FoundingEntity | indicates that a broadcasting company was founded by a specific founding entity |
| case5_concat | wasInOfficeWhile | 728 | True | Individual | Presidency | indicates that an individual held a position during a specific presidency |
| case5_concat | wasMemberOf | 69 | True | HistoricalFigure | SpaceMission | represents the relationship where a historical figure was part of a space mission |
| case5_concat | wasOn | 375 | True | MilitaryPerson | SpaceMission | indicates that a military person participated in a space mission |
| case5_concat | weight | 46 | True | Individual | Weight | indicates that an individuals weight is measured |
| case5_concat | winLeagueTitle | 498 | True | SportsTeam | ProfessionalLeague | indicates that a sports team has won a league title |
| case5_concat | wonChampionship | 293 | True | SportsTeam | League | indicates that a sports team achieved victory in a league organized by a governing body |
| case5_concat | wonLeague | 76 | True | SportsTeam | League | indicates that a sports team has won a league championship |
| case5_concat | wrote | 351 | True | Author | Book | represents the relationship where an author creates a book |
| case5_concat | year | 82 | True | League | Year | indicates that a league takes place in a specific year |
| case5_concat | yearErected | 247 | True | HistoricalMonument | Year | represents the relationship where a monument is associated with a specific year of erection |
| case5_concat | yearInLeague | 128 | True | SportsTeam | Year | indicates that a sports team has been in a league for a specific year |
| case5_concat | yearOfDeath | 909 | True | Individual | Year | indicates that an individual died in a specific year |
| case5_concat | yearOfGraduation | 282 | True | Individual | GraduationYear | indicates that an individual graduated in a specific year |
| case5_concat | youthClub | 101 | True | Athlete | SportsTeam | indicates that an athlete is a member of the youth team of a sports club |
| case5_concat | youthFootballClub | 1026 | True | Athlete | YouthFootballClub | indicates that an athlete was initially nurtured by a youth football club |
| case5_concat | youthTeam | 192 | True | SportsTeam | Athlete | indicates that a sports team has an affiliated youth athlete |
| case6_weighted | CEO | 465 | True | Company | CEO | indicates that a company is led by a chief executive officer |
| case6_weighted | aboveSeaLevel | 925 | True | City | AboveSeaLevel | indicates that a city is located above a certain sea level |
| case6_weighted | absoluteMagnitude | 33 | True | Asteroid | AbsoluteMagnitude | indicates that an asteroid has a specific absolute magnitude |
| case6_weighted | absolute_magnitude | 447 | True | CelestialBody | AbsoluteMagnitude | represents the relationship where an asteroid has a specific brightness measurement |
| case6_weighted | academicStaffSize | 643 | True | EducationalInstitution | EmployeeCount | indicates that an educational institution has a specific number of employees |
| case6_weighted | actedIn | 111 | True | Actor | TelevisionSeries | indicates that an actor starred in a television series |
| case6_weighted | actor | 1086 | True | TelevisionShow | Actor | indicates that a show features actors in its cast |
| case6_weighted | address | 3 | True | ArchitecturalStructure | GeographicLocation | indicates that an architectural structure has a specific physical address |
| case6_weighted | adjacentCounty | 185 | True | County | County | represents the relationship where one county is geographically adjacent to another county |
| case6_weighted | affiliatedTo | 974 | True | EducationalInstitution | University | indicates that an educational institution is associated with a university |
| case6_weighted | affiliatedWith | 643 | True | EducationalInstitution | EducationalInstitution | represents the relationship where an educational institution is affiliated with another educational institution |
| case6_weighted | affiliation | 17 | True | Institute | University | indicates that an educational institution is associated with a university for academic purposes |
| case6_weighted | airedBananaman | 868 | True | BroadcastNetwork | TVSeries | represents the relationship where a broadcast network broadcasts a TV series |
| case6_weighted | airedOn | 124 | True | TVSeries | BroadcastingCompany | indicates that a TV series is broadcasted by a specific broadcasting company |
| case6_weighted | airedShowOn | 345 | True | BroadcastingCompany | EventDate | indicates that a broadcasting company aired a show on a specific date |
| case6_weighted | altitudeAboveSeaLevel | 15 | True | Airport | Altitude | indicates that an airport is at a specific altitude above sea level |
| case6_weighted | annualRevenue | 1157 | True | Company | AnnualRevenue | represents the total revenue generated by a company in a fiscal year |
| case6_weighted | anthem | 225 | True | Monarchy | NationalAnthem | represents the relationship where a monarchy has a national anthem |
| case6_weighted | apoapsis | 33 | True | Asteroid | Apoapsis | indicates that an asteroid has a specific apoapsis distance |
| case6_weighted | apolloCrewMember | 337 | True | HistoricalFigure | SpaceMission | indicates that a historical figure was a crew member of a space mission |
| case6_weighted | architect | 3 | True | ArchitecturalStructure | Architect | indicates that an architectural structure is designed by a professional architect |
| case6_weighted | are | 826 | True | Thing | Thing | indicates that a group of entities share a common identity or classification |
| case6_weighted | area | 200 | True | Country | Area | represents the relationship where a countrys geographical extent is quantified |
| case6_weighted | areaCode | 74 | True | Place | AreaCode | represents the relationship where a place is uniquely identified by a numeric area code |
| case6_weighted | assembledBy | 982 | True | Automobile | AutomotiveCompany | indicates that an automobile is manufactured by an automotive company |
| case6_weighted | assembledIn | 680 | True | Automobile | City | represents the relationship where a vehicle is produced within a city |
| case6_weighted | assemblyLineLocation | 39 | True | Vehicle | City | indicates that a vehicle was produced on an assembly line located within a city |
| case6_weighted | assemblyLocation | 624 | True | Automobile | City | indicates that an automobile is assembled in a specific city |
| case6_weighted | associatedWith | 400 | True | Musician | Musician | indicates that a musician collaborates with another artist in musical projects |
| case6_weighted | attendedSchool | 63 | True | Student | EducationalInstitution | represents the relationship where a student is enrolled in an educational institution |
| case6_weighted | author | 72 | True | Book | Author | indicates that a book is authored by an individual |
| case6_weighted | award | 154 | True | HistoricalFigure | MilitaryAward | indicates that a historical figure received a specific military award |
| case6_weighted | awarded | 599 | True | HistoricalFigure | Medal | represents the relationship where a historical figure receives a distinguished service medal |
| case6_weighted | awardedBy | 349 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure received a military award from a branch of the armed forces |
| case6_weighted | awardedTechnicalCampusStatusTo | 131 | True | GovernmentAgency | EducationalInstitution | represents the relationship where a government agency grants a technical campus status to an educational institution |
| case6_weighted | awardedTo | 154 | True | MilitaryBranch | HistoricalFigure | indicates that a military branch awards a specific historical figure a medal |
| case6_weighted | awardingBody | 615 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure is awarded by a specific military branch |
| case6_weighted | becameProfessional | 582 | True | Individual | Profession | indicates that an individual transitioned into a professional role |
| case6_weighted | beganCareerIn | 893 | True | Musician | Date | indicates that a musician starts their professional career at a specific date |
| case6_weighted | beganMusicalCareer | 400 | True | Musician | Year | represents the relationship where a musician starts their professional music career |
| case6_weighted | birthDate | 13 | True | MilitaryPerson | Date | indicates that a military person was born on a specific date |
| case6_weighted | birthPlace | 28 | True | Politician | City | indicates that a politician was born in a specific city |
| case6_weighted | birthYear | 34 | True | HistoricalFigure | Year | indicates that a historical figure was born in a specific year |
| case6_weighted | bodyStyle | 399 | True | Automobile | BodyStyle | represents the relationship where an automobile has a specific body style |
| case6_weighted | borderingCounty | 906 | True | County | County | indicates that a county shares borders with other counties |
| case6_weighted | born | 364 | True | Astronaut | BirthDate | indicates that an astronaut was born on a specific date |
| case6_weighted | bornIn | 4 | True | Individual | City | indicates that an individual is born in a specific city |
| case6_weighted | bornOn | 30 | True | Athlete | BirthDate | indicates that an athlete was born on a specific date |
| case6_weighted | bornWithin | 357 | True | Individual | Monarchy | indicates that an individual was born within a monarchy |
| case6_weighted | born_on | 805 | True | Astronaut | BirthDate | indicates that an astronaut was born on a specific date |
| case6_weighted | broadcastedBy | 6 | True | TVShow | BroadcastingCompany | indicates that a TV show is broadcast by a specific broadcasting company |
| case6_weighted | broughtUpBy | 250 | True | MediaCompany | AnimatedCharacter | represents the relationship where a media company is associated with a specific animated character |
| case6_weighted | buildStartDate | 965 | True | EducationalBuilding | TemporalValue | indicates that a building was constructed on a specific date |
| case6_weighted | builder | 105 | True | Locomotive | Company | represents the relationship where a locomotive is produced by a manufacturing company |
| case6_weighted | built | 966 | True | HistoricalStructure | Year | indicates that a historical structure was constructed in a specific year |
| case6_weighted | builtBetween | 150 | True | Locomotive | HistoricalPeriod | indicates that a locomotive was constructed within a specific historical time frame |
| case6_weighted | builtBy | 757 | True | EducationalBuilding | Architect | represents the relationship where an educational building is designed by an architect |
| case6_weighted | builtIn | 7 | True | HistoricalStructure | TimePeriod | indicates that a historical structure is constructed in a specific year |
| case6_weighted | builtOn | 278 | True | EducationalBuilding | ConstructionDate | indicates that an educational building was constructed on a specific date |
| case6_weighted | campusLocation | 410 | True | University | Road | indicates that a university is situated on a specific road within its campus |
| case6_weighted | campusStatus | 974 | True | EducationalInstitution | CampusStatus | indicates that an educational institution has been granted a specific status by a governing body |
| case6_weighted | campus_location | 563 | True | EducationalInstitution | Address | indicates that an educational institution has a specific campus location |
| case6_weighted | canBeVaryWith | 67 | True | Dessert | DairyProduct | indicates that a dessert can be prepared with a dairy product |
| case6_weighted | categorization | 501 | True | HistoricalStructure | HistoricResource | indicates that a historical structure is recognized as a resource contributing to the significance of a district |
| case6_weighted | category | 104 | True |  |  |  |
| case6_weighted | ceremonialCounty | 830 | True | Town | CeremonialCounty | represents the relationship where a town is part of a ceremonial county |
| case6_weighted | champion | 246 | True | League | SportsTeam | represents the relationship where a league has a champion sports team |
| case6_weighted | championOf | 659 | True | SportsTeam | League | represents the relationship where a sports team is the champion of a league |
| case6_weighted | champions | 16 | True | SportsTeam | League | indicates that a sports team is the champion of a league |
| case6_weighted | championship | 920 | True | SportsClub | League | indicates that a sports club has won a specific league championship |
| case6_weighted | championships | 629 | True | SportsTeam | Number | indicates that a sports team has won a specific number of championships |
| case6_weighted | channel | 384 | True | TVSeries | BroadcastingCompany | indicates that a TV series is broadcasted on a specific television channel operated by a broadcasting company |
| case6_weighted | character | 688 | True | Actor | TelevisionSeries | indicates that an actor portrays a character in a television series |
| case6_weighted | citizens | 369 | True | Nation | Population | represents the relationship where a nation comprises a specific demographic group |
| case6_weighted | citizenship | 28 | True | Politician | Nation | indicates that a politician holds citizenship in a specific nation |
| case6_weighted | city | 418 | True | EducationalInstitution | City | indicates that an educational institution is located in a specific city |
| case6_weighted | cityManagerTitle | 73 | True | City | CityManager | indicates that a city is led by a city manager |
| case6_weighted | coach | 295 | True | Team | Coach | represents the relationship where a coach leads a sports team |
| case6_weighted | competedIn | 284 | True | SportsTeam | Season | represents the relationship where a sports team participated in a specific season |
| case6_weighted | completedOn | 190 | True | ArchitecturalStructure | CompletionDate | indicates that an architectural structure is finished on a specific completion date |
| case6_weighted | completionDate | 112 | True | Structure | Year | indicates that a building was completed on a specific year |
| case6_weighted | constructedBy | 47 | True | Structure | Architect | represents the relationship where a structure is designed by an architect |
| case6_weighted | constructionPeriod | 47 | True | Structure | Period | indicates that a structure was built within a specific time frame |
| case6_weighted | constructionStart | 361 | True | Facility | Temporal | indicates that a facilitys construction began on a specific date |
| case6_weighted | constructionStartDate | 1121 | True | EducationalBuilding | ConstructionStartDate | indicates that an educational building has a specific start date for construction |
| case6_weighted | constructionStartedOn | 887 | True | Structure | Temporal | indicates that the construction of a constructed facility began on a specific date |
| case6_weighted | contains | 58 | True | SweetDessert | CondensedMilk | indicates that a dessert includes a specific dairy product |
| case6_weighted | containsAdministrativeTerritory |  | False | AdministrativeTerritory | AdministrativeTerritory | Indicates that an administrative territory contains another administrative territory. |
| case6_weighted | containsIngredient | 986 | True | Dish | Nutrition | indicates that a dish includes granola, shredded coconut, and raisins as nutritional ingredients |
| case6_weighted | containsSettlement |  | False | AdministrativeTerritory | Settlement | Indicates that an administrative territory contains a settlement such as a city or town. |
| case6_weighted | containsTeam | 284 | True | League | SportsTeam | represents the relationship where a league includes multiple sports teams |
| case6_weighted | corporateForm | 29 | True | Company | LegalForm | represents the relationship where a company has a specific legal form |
| case6_weighted | cosparId | 416 | True | SpaceMission | CosparId | represents the relationship where a space mission is uniquely identified by a COSPAR ID |
| case6_weighted | country | 3 | True | EducationalInstitution | Country | indicates that an educational institution is located in a specific country |
| case6_weighted | countryOfBirth | 356 | True | HistoricalFigure | Country | represents the relationship where a historical figure is born in a specific country |
| case6_weighted | countryOfCitizenship | 344 | True | Politician | Country | indicates that a politician is a citizen of a specific country |
| case6_weighted | countryOfDeath | 689 | True | GeopoliticalEntity | GeopoliticalEntity | indicates that a sovereign state is the place where an individual died |
| case6_weighted | countryOfOrigin | 316 | True | Musician | Country | indicates that a musician originates from a specific country |
| case6_weighted | countryOrigin | 369 | True | Sweet | Nation | indicates that a sweet dessert originates from a specific nation |
| case6_weighted | county | 7 | True | HistoricalStructure | County | indicates that a historical structure is situated within a county |
| case6_weighted | created | 459 | True | Author | Book | represents the relationship where an author produces a literary work |
| case6_weighted | creator | 6 | True | TVShow | Creator | represents the relationship where a TV show is created by a specific creator |
| case6_weighted | crew | 703 | True | HistoricalFigure | SpaceMission | indicates that a historical figure was a member of a specific space mission |
| case6_weighted | crewMember | 1117 | True | SpaceMission | HistoricalFigure | represents the relationship where a space mission has a crew member who is a historical figure |
| case6_weighted | crewMemberOf | 827 | True | Astronaut | SpaceMission | represents the relationship where an astronaut serves as a crew member on a space mission |
| case6_weighted | currency | 24 | True | GeopoliticalEntity | MonetaryUnit | indicates that a country uses a specific currency for transactions |
| case6_weighted | currentAssemblyLocation | 697 | True | Automobile | City | indicates that an automobile is currently assembled in a specific city |
| case6_weighted | currentClub | 30 | True | Athlete | FootballClub | indicates that an athlete is currently affiliated with a football club |
| case6_weighted | currentDirector | 835 | True | EducationalInstitution | Educator | indicates that an educational institution has a current director who is an educator |
| case6_weighted | currentLeader | 699 | True | Nation | Politician | represents the relationship where a nation is led by a political leader |
| case6_weighted | currentLocation | 187 | True | Company | Country | indicates that a company is headquartered in a specific country |
| case6_weighted | currentOwner | 588 | True | EducationalBuilding | EducationalInstitution | indicates that an educational building is owned by an educational institution |
| case6_weighted | currentPosition | 156 | True | Politician | PoliticalOffice | represents the relationship where a politician holds a current political office position |
| case6_weighted | currentSenator | 476 | True | State | Politician | represents the relationship where a state is governed by a current senator |
| case6_weighted | currentTeam | 42 | True | Player | Team | represents the relationship where a player is currently associated with a specific team |
| case6_weighted | currentTenant | 730 | True | EducationalBuilding | EducationalInstitution | indicates that an educational building houses an educational institution |
| case6_weighted | currentTenants | 3 | True | ArchitecturalStructure | EducationalInstitution | indicates that an architectural structure is currently occupied by an educational institution |
| case6_weighted | currentlyPlaysFor | 95 | True | Athlete | SportsTeam | indicates that an athlete is currently affiliated with a sports team |
| case6_weighted | dateOfBirth | 25 | True | Individual | BirthDate | indicates that an individual has a specific birth date |
| case6_weighted | dateOfDeath | 173 | True | Individual | DeathDate | indicates that an individual died on a specific date |
| case6_weighted | dateOfGraduation | 866 | True | HistoricalFigure | AcademicYear | indicates that a historical figure graduated from an academic institution in a specific year |
| case6_weighted | dateOfRetirement | 154 | True | HistoricalFigure | RetirementDate | indicates that a historical figure retired on a specific date |
| case6_weighted | dateOfRole | 633 | True | HistoricalFigure | HistoricalYear | indicates that a historical figure held a role in a specific year |
| case6_weighted | deathCause | 640 | True | Individual | Death | indicates that an individuals death is caused by a natural or medical condition |
| case6_weighted | deathDate | 93 | True | Individual | DeathDate | indicates that an individual has a specific death date |
| case6_weighted | deathPlace | 28 | True | Politician | Nation | indicates that a politician died in a specific nation |
| case6_weighted | debutTeam | 425 | True | Player | Team | indicates that a player made their initial appearance for a specific team |
| case6_weighted | degree | 282 | True | Individual | Degree | indicates that an individual earned a specific academic degree |
| case6_weighted | designatedAs | 643 | True | EducationalInstitution | CampusDesignation | represents the relationship where an educational institution is given a specific designation or classification |
| case6_weighted | designatedTechnicalCampusStatusTo | 143 | True | Council | Institute | indicates that a council formally recognizes a technical education institution as a campus |
| case6_weighted | diedIn | 4 | True | Individual | Country | indicates that an individual dies in a specific country |
| case6_weighted | directedBy | 254 | True | EducationalInstitution | Educator | indicates that an educational institution is led by an educator |
| case6_weighted | direction | 365 | True | AdministrativeDivision | GeographicalDirection | indicates that a territorial division is geographically positioned relative to another |
| case6_weighted | director | 131 | True | EducationalInstitution | Educator | represents the relationship where an educational institution is led by an educator |
| case6_weighted | discovered | 182 | True | Astronomer | AstronomicalBody | indicates that an astronomer identifies a celestial body |
| case6_weighted | discoveredBy | 33 | True | Asteroid | Astronomer | indicates that an asteroid is identified by an astronomer |
| case6_weighted | discoveryDate | 33 | True | Asteroid | Date | indicates that an asteroids discovery is recorded with a specific date |
| case6_weighted | doctoralStudentPopulation | 932 | True | University | StudentPopulation | indicates that a university has a specific number of doctoral students |
| case6_weighted | doctoralStudents | 66 | True | University | DoctoralStudents | indicates that a university has a specific number of students enrolled in doctoral programs |
| case6_weighted | draftPick | 518 | True | Athlete | DraftPick | indicates that an athlete is selected as a draft pick |
| case6_weighted | draftPickNumber | 1148 | True | Athlete | DraftPickNumber | indicates that an athlete is assigned a specific draft pick number |
| case6_weighted | earnings | 85 | True | Company | Earnings | indicates that a company generates financial income over a year |
| case6_weighted | eat | 790 | True | Dessert | Type | indicates that a dessert is consumed as a type of food |
| case6_weighted | educate | 537 | True | University | StudentCount | indicates that a university enrolls a specific number of students |
| case6_weighted | educatedAt | 707 | True | FootballClub | Athlete | indicates that a football club has an athlete as a former member |
| case6_weighted | educates | 257 | True | University | StudentPopulation | indicates that a university enrolls a total number of students |
| case6_weighted | education | 53 | True | HistoricalFigure | Degree | indicates that a historical figure has earned a formal academic degree |
| case6_weighted | elevation | 71 | True | Airport | Elevation | indicates that an airport has a specific elevation measurement above sea level |
| case6_weighted | elevationAboveSeaLevel | 41 | True | Airport | ElevationAboveSeaLevel | indicates that an airport has a specific elevation above sea level measurement |
| case6_weighted | endDateConstruction | 946 | True | Structure | Temporal | indicates that a building was completed at a specific point in time |
| case6_weighted | endedManufacturingOf | 325 | True | Automaker | AutomobileModel | indicates that an automaker ceases production of a specific vehicle model |
| case6_weighted | engine | 350 | True | Locomotive | Engine | indicates that a locomotive is equipped with a particular type of engine |
| case6_weighted | engineType | 65 | True |  |  |  |
| case6_weighted | epoch | 64 | True | Asteroid | Time | represents the relationship where an asteroid reaches a specific epoch in its orbit |
| case6_weighted | epochDate | 958 | True | CelestialBody | Date | indicates that a celestial body has a specific reference date |
| case6_weighted | erectedIn | 638 | True | Monument | State | indicates that a monument is erected in a specific state |
| case6_weighted | established | 48 | True | HistoricalMonument | TimePeriod | indicates that a historical monument is founded in a specific year |
| case6_weighted | establishedIn | 146 | True | EducationalInstitution | Year | indicates that an educational institution was founded in a specific year |
| case6_weighted | establishmentYear | 138 | True | Monument | Year | indicates that a monument was established in a specific year |
| case6_weighted | ethnicGroup | 4 | True | Country | Group | represents the relationship where a country has a specific ethnic group |
| case6_weighted | ethnonym | 735 | True | Nation | EthnicGroup | represents the relationship where a nation has an ethnonym |
| case6_weighted | extinctionDate | 558 | True | AutomobileBrand | Year | represents the relationship where an automobile brand ceased operations on a specific year |
| case6_weighted | firstAired | 6 | True | TVShow | EventDate | indicates that a TV show marks its premiere on a specific date |
| case6_weighted | firstAiredBy | 698 | True | TelevisionShow | BroadcastingCompany | indicates that a television show is broadcasted by a specific broadcasting company |
| case6_weighted | firstAiredOn | 21 | True | Program | EventDate | indicates that a program was first broadcasted on a specific date |
| case6_weighted | firstAppearance | 260 | True | Film | AnimatedCharacter | represents the relationship where a film features its initial appearance of an animated character |
| case6_weighted | firstAppearedAsFilmCharacterIn | 779 | True | FilmCharacter | Film | represents the relationship where a characters first appearance in a film is specified |
| case6_weighted | firstAppearedIn | 824 | True | AnimatedCharacter | Film | represents the relationship where an animated characters debut is in a movie |
| case6_weighted | firstBroadcast | 250 | True | AnimatedCharacter | EventDate | indicates that an animated character had its first broadcast on a specific date |
| case6_weighted | firstProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was first manufactured in a specific year |
| case6_weighted | followedBy | 241 | True | Book | Book | indicates that one book series continues another in a narrative sequence |
| case6_weighted | follows | 585 | True | Book | Book | indicates that one book comes after another in a series |
| case6_weighted | foodServedAsDessert | 811 | True | Nation | Dessert | indicates that a nation serves a specific dessert as a dessert |
| case6_weighted | formerClub | 616 | True | Player | FootballClub | represents the relationship where a player was previously affiliated with a football club |
| case6_weighted | formerTeam | 186 | True | Player | Team | represents the relationship where a player was formerly part of a team |
| case6_weighted | formerlyPlayedFor | 782 | True | Athlete | SportsTeam | indicates that an athlete previously played for a sports team |
| case6_weighted | formerlyPlayedWith | 318 | True | Athlete | SportsTeam | indicates that an athlete previously played for a sports team |
| case6_weighted | foundIn | 19 | True | DessertFood | Country | represents the relationship where a dessert food item is located within a specific country |
| case6_weighted | founded | 114 | True | Company | Date | indicates that a company was established on a specific date |
| case6_weighted | foundedBy | 698 | True | BroadcastingCompany | FoundingFather | indicates that a broadcasting company was established by a founding father |
| case6_weighted | founder | 62 | True | Company | Founder | represents the relationship where a company is initiated and managed by a founder |
| case6_weighted | founding | 691 | True | City | HistoricalFigure | represents the relationship where a city is founded by a historical figure |
| case6_weighted | foundingDate | 22 | True | PharmaceuticalCompany | FoundingDate | indicates that a pharmaceutical company was established on a specific founding date |
| case6_weighted | foundingEntity | 221 | True | BroadcastingCompany | FoundingEntity | represents the relationship where a broadcasting company is established by a founding entity |
| case6_weighted | foundingFather | 1014 | True | BroadcastingCompany | FoundingFather | represents the relationship where a broadcasting company was established by a founding father |
| case6_weighted | foundingPlace | 114 | True | Company | City | indicates that a company was founded in a specific city |
| case6_weighted | foundingYear | 1024 | True | Aerodrome | Year | indicates that an aerodrome was founded in a specific year |
| case6_weighted | from | 936 | True | Musician | Thing | indicates that a musician is associated with a specific geographic entity |
| case6_weighted | fullAddress | 392 | True | Institute | Address | indicates that an institute has a specific full physical address |
| case6_weighted | fullName | 203 | True | State | Name | indicates that a state has a formal name |
| case6_weighted | full_name | 246 | True | SportsTeam | SportsTeam | indicates that a sports team has a formal name |
| case6_weighted | gaveStatusBy | 857 | True | EducationalInstitution | EducationalAuthority | indicates that an educational institution is granted a status by an educational authority |
| case6_weighted | genre | 91 | True | TV_series | Series | indicates that a TV series belongs to a specific series category |
| case6_weighted | givenStatusBy | 1013 | True | EducationalInstitution | EducationalAuthority | indicates that an educational institution receives a status designation from an educational authority |
| case6_weighted | giverOfStatus | 1070 | True | EducationalInstitution | GovernmentAgency | indicates that a government agency grants a designation or accreditation to an educational institution |
| case6_weighted | governingBody | 748 | True | City | Position | indicates that a city is governed by a specific leadership position |
| case6_weighted | governmentForm | 1036 | True | StateFormOfGovernment | UnitaryState | indicates that a state form of government is characterized by a centralized system of governance |
| case6_weighted | governmentType | 1 | True |  |  |  |
| case6_weighted | governor | 925 | True | City | GovernmentBody | indicates that a city is governed by a government body |
| case6_weighted | graduatedFrom | 512 | True | HistoricalFigure | EducationalInstitution | indicates that a historical figure received a degree from an educational institution |
| case6_weighted | graduationYear | 242 | True | HistoricalFigure | GraduationYear | indicates that a historical figure completed an educational program in a specific year |
| case6_weighted | ground | 16 | True | Stadium | SportsTeam | indicates that a stadium hosts a sports team |
| case6_weighted | grounds | 675 | True | SportsTeam | Stadium | indicates that a sports team has a specific ground or stadium |
| case6_weighted | hadCampusIn | 492 | True | University | City | indicates that a university had its campus within a specific city |
| case6_weighted | has | 48 | True | AdministrativeDivision | AdministrativeDivision | indicates that a territorial division contains another territorial division |
| case6_weighted | hasBird | 282 | True | State | Species | represents the relationship where a state is associated with a specific bird species |
| case6_weighted | hasCylinderCount | 426 | True | Locomotive | CylinderCount | indicates that a locomotive has a specific number of cylinders |
| case6_weighted | hasDessert | 791 | True | City | SweetDish | indicates that a city has a specific dessert dish |
| case6_weighted | hasDoctoralStudents | 1107 | True | University | NumberOfStudents | indicates that a university has a specific number of doctoral students |
| case6_weighted | hasFood | 945 | True | Nation | Dessert | indicates that a nation includes a specific type of food in its culinary offerings |
| case6_weighted | hasIngredient | 892 | True | Dessert | Ingredient | indicates that a dessert contains a specific ingredient |
| case6_weighted | hasItem | 171 | True | UrbanCenter | SweetFood | represents the relationship where an urban center has another specific type of sweet food item |
| case6_weighted | hasMember | 360 | True | Band | Musician | represents the relationship where a band comprises a musician |
| case6_weighted | hasNativeBird | 505 | True | State | Bird | represents the relationship where a state is home to a specific native bird species |
| case6_weighted | hasOfficial | 493 | True | State | Official | represents the relationship where a state appoints an official to lead its administration |
| case6_weighted | hasPart | 727 | True | GeographicArea | GeographicArea | represents the relationship where one geographic area contains another |
| case6_weighted | hasPopulationDensity | 669 | True | Country | PopulationDensity | represents the relationship where a country has a specific population density |
| case6_weighted | hasProperty | 836 | True | City | Monument | indicates that a city has a specific historical or commemorative monument |
| case6_weighted | hasSenator | 789 | True | State | Politician | represents the relationship where a state has a senator |
| case6_weighted | hasSubsidiary | 85 | True | Company | Subsidiary | represents the relationship where a company maintains a subsidiary organization |
| case6_weighted | hasTeam | 524 | True | ProfessionalLeague | SportsClub | represents the relationship where a professional league has a team belonging to a sports club |
| case6_weighted | hasUndergraduateStudents | 462 | True | University | UndergraduateStudents | indicates that a university enrolls a specific number of undergraduate students |
| case6_weighted | hasVariation | 985 | True | Dessert | Dessert | indicates that a dessert has a variation of another dessert |
| case6_weighted | headquarteredIn | 386 | True | University | City | indicates that a university is geographically located within a specific city |
| case6_weighted | headquarters | 111 | True | TelevisionNetwork | Headquarters | indicates that a television network has its administrative center in a specific building |
| case6_weighted | headquartersLocation | 99 | True | AirlineCompany | City | indicates that an airline company has its headquarters in a city |
| case6_weighted | height | 90 | True | Athlete | Height | indicates that an athlete has a specific height measurement |
| case6_weighted | heldOfficeWhile | 862 | True | Politician | Politician | indicates that a politician held office during the tenure of another politician |
| case6_weighted | homeGround | 88 | True | SportsTeam | Stadium | indicates that a sports team has a designated home ground venue |
| case6_weighted | icaoIdentifier | 355 | True | Aerodrome | ICAOIdentifier | indicates that an aerodrome is assigned a unique ICAO identifier |
| case6_weighted | icaoLocationIdentifier | 14 | True | Aerodrome | ICAOIdentifier | represents the relationship where an aerodrome is assigned a unique ICAO identifier |
| case6_weighted | inBand | 630 | True | Musician | Band | indicates that a musician is part of a band organization |
| case6_weighted | inOfficeWhile | 950 | True | Politician | Politician | represents the relationship where one politician serves while another is in office |
| case6_weighted | inOfficeWith | 344 | True | Politician | Politician | indicates that two politicians held office simultaneously |
| case6_weighted | industry | 187 | True | Company | BuildingMaterials | represents the relationship where a company operates within a specific industry category |
| case6_weighted | industryClassification | 559 | True | EnergyCompany | EnergySector | represents the relationship where an energy company belongs to the energy industry sector |
| case6_weighted | ingredient | 302 | True | Dessert | Ingredient | represents the relationship where a dessert includes various components |
| case6_weighted | ingredients | 24 | True | DessertFood | FoodIngredients | indicates that a dessert food is composed of specific ingredients |
| case6_weighted | inhabit | 790 | True | Nation | Country | represents the relationship where a nation is inhabited by a specific country |
| case6_weighted | inhabitant | 24 | True | GeopoliticalEntity | HumanPopulation | represents the relationship where a country is populated by its inhabitants |
| case6_weighted | inhabitants | 67 | True | Country | Population | indicates that a country is inhabited by a population |
| case6_weighted | inhabitedBy | 485 | True | Mexico | HumanPopulation | represents the relationship where the inhabitants of Mexico are the Mexicans |
| case6_weighted | inhabits | 853 | True | State | Bird | represents the relationship where a state is home to a specific bird species |
| case6_weighted | is | 826 | True | Thing | Thing | represents the relationship where an entity belongs to a specific category |
| case6_weighted | isA | 19 | True |  |  |  |
| case6_weighted | isAffiliatedTo | 133 | True |  |  |  |
| case6_weighted | isAffiliatedWith | 198 | True |  |  |  |
| case6_weighted | isAnEthnicGroup | 1034 | True |  |  |  |
| case6_weighted | isAssociatedWith | 131 | True |  |  |  |
| case6_weighted | isBasedAt | 345 | True | BroadcastingCompany | Building | indicates that a broadcasting company operates from a physical workplace |
| case6_weighted | isBasedIn | 51 | True | Airport | City | indicates that an airport is geographically located within a city |
| case6_weighted | isCapitalOf | 669 | True | Country | Country | represents the relationship where a country is the capital of itself |
| case6_weighted | isCategorizedAs | 48 | True | HistoricalMonument | HistoricProperty | indicates that a historical monument is classified as a significant property |
| case6_weighted | isCategory | 836 | True |  |  |  |
| case6_weighted | isChampion | 82 | True | SportsClub | BooleanValue | indicates that a sports club is the champion of a league |
| case6_weighted | isChampionOf | 211 | True | SportsClub | League | indicates that a sports club is the winner of a league competition |
| case6_weighted | isChiefOf | 866 | True | HistoricalFigure | AerospaceAgency | indicates that a historical figure leads an aerospace agency |
| case6_weighted | isContributing_Property | 873 | True | HistoricalMonument | TrueValue | represents the relationship where a historical monument is considered significant or contributing to a site |
| case6_weighted | isDessert | 791 | True | SweetDish | LogicalValue | represents the relationship where a dessert dish is classified as a dessert |
| case6_weighted | isEthnicGroup | 427 | True | Community | Nation | represents the relationship where an ethnic group is part of a national entity |
| case6_weighted | isEthnicGroupIn | 728 | True | EthnicGroup | Country | indicates that an ethnic group is geographically located within a country |
| case6_weighted | isFoundationPlace | 499 | True | FoundationPlace | FoundationPlace | indicates that a FoundationPlace serves as the origin or basis of another FoundationPlace |
| case6_weighted | isFrom | 725 | True | Individual | Thing | indicates that an individual is from a specific entity |
| case6_weighted | isHomeTo | 466 | True | EducationalBuilding | EducationalInstitution | indicates that an educational building houses an educational institution |
| case6_weighted | isInhabitedBy | 860 | True | Nation | Population | indicates that a nation is populated by a specific demographic group |
| case6_weighted | isLeaderIn | 1160 | True | Politician | Nation | indicates that a politician leads a nation |
| case6_weighted | isLeaderOf | 303 | True | Politician | Thing | indicates that a politician holds leadership over a specific entity |
| case6_weighted | isLeagueChampion | 189 | True | SportsTeam | ChampionStatus | indicates that a sports team is the current champion of a league |
| case6_weighted | isLocatedAt | 650 | True | EducationalInstitution | City | indicates that an educational institution is physically situated within a city |
| case6_weighted | isLocatedIn | 48 | True | HistoricalMonument | Municipality | indicates that a historical monument is located within a populated place |
| case6_weighted | isLocationOf | 969 | True | Country | Population | represents the relationship where a country is the location of its population |
| case6_weighted | isManagedBy | 367 | True | City | GovernmentPosition | indicates that a city is managed by a specific government position |
| case6_weighted | isMemberOf | 152 | True | Politician | PoliticalParty | indicates that a politician belongs to a political party organization |
| case6_weighted | isNear | 744 | True | HistoricalMonument | County | indicates that a historical monument is located near another county |
| case6_weighted | isPartOf | 1 | True | City | State | indicates that a city is administratively part of a state |
| case6_weighted | isServedAs | 305 | True | FoodItem | MealComponent | represents the relationship where a food item is part of a meal course |
| case6_weighted | isServedBy | 354 | True | Autodrome | Aerodrome | indicates that an autodrome is served by another location |
| case6_weighted | isStarOf | 345 | True | Actor | TVShow | indicates that an actor performs in a television show |
| case6_weighted | isType | 1077 | True |  |  |  |
| case6_weighted | isWestOf | 836 | True | City | County | indicates that a city is located west of a county |
| case6_weighted | keyPerson | 461 | True | PharmaceuticalCompany | Executive | represents the relationship where a pharmaceutical company is led by a high-ranking executive |
| case6_weighted | keyPersonAt | 1113 | True | KeyPerson | MassMediaCompany | indicates that a key person holds a significant role within a mass media company |
| case6_weighted | keyPersonFor | 609 | True | KeyPerson | Company | indicates that a key person oversees a company |
| case6_weighted | language | 340 | True | Nation | ModernLanguage | represents the relationship where a nation employs a modern form of a language |
| case6_weighted | lastAired | 366 | True | TVSeries | EventDate | indicates that a TV series concludes on a specific event date |
| case6_weighted | lastAiredOn | 167 | True | Program | Date | indicates that a program was last aired on a specific date |
| case6_weighted | lastProducedOn | 39 | True | Vehicle | Year | represents the relationship where a vehicle was last manufactured in a specific year |
| case6_weighted | laterCrewMemberOf | 602 | True | HistoricalFigure | SpaceMission | indicates that a historical figure serves as a crew member on a space mission |
| case6_weighted | leader | 196 | True | City | Politician | represents the relationship where a city is governed by a political leader |
| case6_weighted | leaderName | 251 | True | City | Leader | represents the relationship where a city is led by a specific person |
| case6_weighted | leaderTitle | 1 | True | City | LeaderTitle | indicates that a city has a leadership role title |
| case6_weighted | leadershipTitle | 280 | True | Country | LeadershipRole | indicates that a country has a specific title for its leadership role |
| case6_weighted | league | 16 | True | SportsTeam | League | indicates that a sports team competes in a specific league |
| case6_weighted | leagueTitle | 975 | True | SportsTeam | League | indicates that a sports team competes in a specific league title |
| case6_weighted | length | 2 | True | Locomotive | Length | represents the relationship where a locomotives physical dimension is defined |
| case6_weighted | locatedAboveSeaLevel | 83 | True | Airport | Altitude | indicates that an airport is at a specific elevation above sea level |
| case6_weighted | locatedAt | 643 | True | EducationalInstitution | Address | represents the specific address or location of an educational institution |
| case6_weighted | locatedIn | 464 | True | Dessert | Country | indicates that a dessert is found in a specific country |
| case6_weighted | locatedInAdministrativeTerritory |  | False | Location | AdministrativeTerritory | Indicates that a location is located within a specific administrative territorial entity. |
| case6_weighted | locatedInCountry | 43 | True | Location | Country | Indicates that a location is located in a country. |
| case6_weighted | location | 0 | True | Company | City | represents the relationship where a companys physical presence is located within a city |
| case6_weighted | locationCity | 872 | True | BroadcastingCompany | City | indicates that a broadcasting company is headquartered in a specific city |
| case6_weighted | locationElevation | 56 | True | Aerodrome | Elevation | indicates that an aerodrome has a specific elevation above sea level |
| case6_weighted | locationInTimezone | 852 | True | City | Zone | indicates that a city is located in a specific time zone |
| case6_weighted | locationOf | 498 | True | Stadium | SportsTeam | indicates that a stadium is the home ground of a sports team |
| case6_weighted | locationOfBroadcast | 167 | True | Program | Building | indicates that a program is broadcast from a specific building |
| case6_weighted | locationOfDeath | 173 | True | Country | Country | indicates that a country is the location of an individual's death |
| case6_weighted | locationOfFounding | 808 | True | Company | City | indicates that a company was founded in a specific city location |
| case6_weighted | locationOfManufacture | 580 | True | Automobile | City | indicates that an automobile is manufactured in a specific city |
| case6_weighted | locationOfOccurrence | 449 | True | Ingredient | Country | indicates that an ingredient is found within a specific country |
| case6_weighted | locationOfProduction | 199 | True | Automobile | City | indicates that an automobile was produced in a specific city |
| case6_weighted | locationRelation | 78 | True | County | SpatialRelation | represents the relationship where a county is situated relative to another county in a north-south direction |
| case6_weighted | longName | 174 | True | Nation | OfficialName | represents the relationship where a nations long name corresponds to its official name |
| case6_weighted | mainDishType | 421 | True |  |  |  |
| case6_weighted | mainIngredient | 329 | True | Dessert | DairyProduct | indicates that a dessert contains raisins |
| case6_weighted | mainOwner | 757 | True | EducationalBuilding | EducationalInstitution | represents the relationship where an educational building is owned by an educational institution |
| case6_weighted | mainProduct | 27 | True | Company | Software | represents the relationship where a company specializes in creating software products |
| case6_weighted | makes | 22 | True | PharmaceuticalCompany | Medicine | indicates that a pharmaceutical company produces medical products |
| case6_weighted | makesProduct | 627 | True | Company | Software | indicates that a company produces software products |
| case6_weighted | manager | 5 | True | SportsTeam | Manager | indicates that a sports team is led by a manager |
| case6_weighted | managerOfCurrentTeam | 572 | True | Athlete | Manager | indicates that an athlete has a manager for their current team |
| case6_weighted | managerTitle | 29 | True | Company | ManagerTitle | indicates that a company is managed by a specific title |
| case6_weighted | manages | 192 | True | Athlete | Coach | represents the relationship where an athlete oversees a coaching role |
| case6_weighted | manufacturer | 150 | True | Locomotive | Manufacturer | indicates that a locomotive is produced by a specific manufacturer |
| case6_weighted | marriage | 640 | True | Individual | Individual | indicates that two individuals are legally or socially united in marriage |
| case6_weighted | memberOf | 30 | True | Athlete | YouthTeam | indicates that an athlete is a member of a youth sports team |
| case6_weighted | mission | 25 | True | Individual | SpaceMission | indicates that an individual participates in a spaceflight mission |
| case6_weighted | missionParticipatedIn | 514 | True | Astronaut | SpaceMission | indicates that an astronaut is involved in multiple space missions |
| case6_weighted | monumentCategory | 955 | True |  |  |  |
| case6_weighted | monumentLocation | 955 | True | MilitaryUnit | County | represents the relationship where a military units monument is located within a county |
| case6_weighted | movedTo | 1161 | True | Company | Country | indicates that a company relocated to a specific country |
| case6_weighted | municipality | 7 | True | HistoricalStructure | City | indicates that a historical structure is located within a city |
| case6_weighted | name | 479 | True | Stadium | Stadium | indicates that a stadium has a specific name |
| case6_weighted | nameOfGround | 659 | True | Stadium | SportsTeam | represents the relationship where a stadium is named after a sports team |
| case6_weighted | nationalAnthem | 269 | True | Government | NationalAnthem | represents the relationship where a government holds a national anthem |
| case6_weighted | nationality | 11 | True | Individual | Country | indicates that an individual belongs to a specific country |
| case6_weighted | nativeOf | 477 | True | State | Bird | indicates that a state is the native home of a bird species |
| case6_weighted | nativeState | 884 | True | Bird | State | represents the relationship where a bird species is native to a specific state |
| case6_weighted | nearbyPlace | 966 | True | County | County | indicates that a county has another county nearby |
| case6_weighted | neighbor | 138 | True | County | County | represents the relationship where a county is geographically adjacent to another county |
| case6_weighted | netIncome | 149 | True | Company | NetIncome | represents the relationship where a companys net income is a specific financial metric |
| case6_weighted | network | 91 | True | TV_series | BroadcastingCompany | indicates that a TV series is broadcasted by a broadcasting company |
| case6_weighted | nickname | 88 | True | SportsTeam | Nickname | represents the relationship where a sports team has a distinctive nickname |
| case6_weighted | northNeighbour | 165 | True | County | County | indicates that a county is geographically located north of another county |
| case6_weighted | northOf | 528 | True | County | County | indicates that one county is geographically situated north of another |
| case6_weighted | numberOfAcademicStaff | 522 | True | EducationalInstitution | NumberOfStaff | indicates that an educational institution has a total number of academic staff |
| case6_weighted | numberOfDoctoralStudents | 237 | True | University | Number_of_DoctoralStudents | indicates that a university has a specific count of doctoral students enrolled |
| case6_weighted | numberOfEmployees | 114 | True | Company | Number | indicates that a company has a specific number of employees |
| case6_weighted | numberOfMembers | 5 | True | SportsTeam | Number | indicates that a sports team has a specific number of members |
| case6_weighted | numberOfPages | 72 | True | Book | Pages | indicates that a book has a specific number of pages |
| case6_weighted | numberOfPostgraduateStudents | 939 | True | University | NumberOfPostgraduateStudents | indicates that a university has a specific number of postgraduate students |
| case6_weighted | numberOfStaff | 900 | True | University | Number | indicates that a university employs a specific number of staff members |
| case6_weighted | numberOfStaffMembers | 237 | True | University | Number_of_StaffMembers | indicates that a university has a specific number of staff members employed |
| case6_weighted | numberOfStudents | 66 | True | University | StudentCount | indicates that a university has a total count of students including various levels and staff members |
| case6_weighted | numberOfUndergraduateStudents | 118 | True | University | Number | indicates that a university has a specific count of undergraduate students |
| case6_weighted | numberOfUndergraduates | 654 | True | EducationalInstitution | StudentCount | indicates that an educational institution has a specific number of undergraduate students |
| case6_weighted | occupation | 13 | True | MilitaryPerson | MilitaryOccupation | indicates that a military person holds a specific military role |
| case6_weighted | offersProduct | 525 | True | MediaCompany | Software | represents the relationship where a media company provides software products |
| case6_weighted | offersServices | 737 | True | Company | WebServices | represents the relationship where a company provides services related to the World Wide Web |
| case6_weighted | offersSport | 643 | True | EducationalInstitution | Activity | indicates that an educational institution provides a specific sport as part of its curriculum or extracurricular activities |
| case6_weighted | officeHolder | 28 | True | Politician | Politician | indicates that a politician holds a position equivalent to another politician |
| case6_weighted | officeStartDate | 885 | True | HistoricalFigure | Year | indicates that a historical figure began holding an administrative role in a specific year |
| case6_weighted | officialLanguage | 183 | True | State | OfficialLanguage | represents the relationship where a state has a primary official language |
| case6_weighted | officialName | 1162 | True | Nation | OfficialName | represents the relationship where a nations official name is its primary identifier |
| case6_weighted | operatedBy | 10 | True | Airbase | MilitaryBranch | indicates that an airbase is managed by a military branch |
| case6_weighted | operates | 92 | True | Company | Airport | indicates that a company manages and maintains an airport facility |
| case6_weighted | operatingArea | 802 | True | Company | Country | represents the relationship where a company operates within a specific country |
| case6_weighted | operatingEntity | 942 | True | Airbase | MilitaryBranch | represents the relationship where an airbase is managed by a military branch |
| case6_weighted | operatingOrganisation | 180 | True |  |  |  |
| case6_weighted | operatingOrganisationFor | 463 | True |  |  |  |
| case6_weighted | operatingOrganization | 132 | True | Aerodrome | OperatingOrganization | represents the relationship where an aerodrome is managed by an operating organization |
| case6_weighted | operator | 40 | True | Airport | AeronauticsCompany | indicates that an airport is managed by an aeronautics company |
| case6_weighted | orbitalPeriod | 33 | True | Asteroid | OrbitalPeriod | indicates that an asteroid has a specific orbital period |
| case6_weighted | orbital_period | 135 | True | Asteroid | OrbitalPeriod | indicates that an asteroid has a duration for its orbit around its primary body |
| case6_weighted | origin | 630 | True | Musician | City | indicates that a musician originates from a specific city |
| case6_weighted | originCountry | 108 | True | Musician | Nation | indicates that a musician originates from a sovereign state |
| case6_weighted | otherTeam | 395 | True | Athlete | SportsTeam | indicates that an athlete is associated with another sports team |
| case6_weighted | ownedBuilding | 588 | True | EducationalInstitution | EducationalBuilding | indicates that an educational institution owns a specific educational building |
| case6_weighted | ownedBy | 374 | True | Structure | EducationalInstitution | indicates that a structure is owned by an educational institution |
| case6_weighted | owner | 190 | True | ArchitecturalStructure | EducationalInstitution | indicates that an architectural structure is owned by an educational institution |
| case6_weighted | owns | 9 | True | EducationalInstitution | EducationalFacility | indicates that an educational institution possesses a specific educational facility |
| case6_weighted | parent | 111 | True | Actor | Daughter | indicates that an actor has a daughter |
| case6_weighted | parentCompany | 609 | True | Company | Company | represents the relationship where a company is the parent entity of another company |
| case6_weighted | partOf | 977 | True | Astronaut | SpaceMission | represents the relationship where an astronaut is part of a spaceflight undertaking |
| case6_weighted | partOfMission | 897 | True | MilitaryPerson | SpaceMission | indicates that a military person is part of a specific space mission |
| case6_weighted | participatedIn | 220 | True | Fighter_pilot | SpaceMission | represents the relationship where a fighter pilot participates in a space mission |
| case6_weighted | people | 1093 | True | Region | Nationality | represents the relationship where a region is inhabited by a specific nationality |
| case6_weighted | peopleName | 171 | True | Nation | PeopleGroup | represents the relationship where a nation has a specific name for its people |
| case6_weighted | periapsis | 49 | True | Asteroid | Periapsis | indicates that an asteroid has a specific periapsis distance |
| case6_weighted | placeOfBirth | 141 | True | Individual | BirthPlace | indicates that an individual was born in a specific geographic location |
| case6_weighted | placeOfDeath | 154 | True | HistoricalFigure | State | indicates that a historical figure died in a specific state |
| case6_weighted | placeOfOrigin | 52 | True | Individual | State | indicates that an individuals place of origin is within a specific state |
| case6_weighted | placeOfUpbringing | 722 | True | Individual | Country | indicates that an individual grew up in a sovereign country |
| case6_weighted | playInLeague | 319 | True | SportsTeam | ProfessionalLeague | represents the relationship where a sports team is affiliated with a professional sports league |
| case6_weighted | playedFor | 95 | True | Athlete | SportsTeam | indicates that an athlete competes for a sports team |
| case6_weighted | playedIn | 179 | True | SportsClub | Year | indicates that a sports club participated in a competition in a specific year |
| case6_weighted | playedInLeague | 479 | True | SportsTeam | League | represents the relationship where a sports team competes in a league |
| case6_weighted | playedInSeason | 76 | True | SportsTeam | Year | indicates that a sports team competes in a specific season |
| case6_weighted | playedWith | 20 | True | Musician | Band | indicates that a musician is a member of a band |
| case6_weighted | playground | 1101 | True | SportsClub | Stadium | indicates that a sports club has a designated sports facility |
| case6_weighted | playsIn | 566 | True | SportsTeam | ProfessionalLeague | indicates that a sports team competes in a professional league |
| case6_weighted | playsInstrument | 50 | True | Musician | MusicalInstrument | indicates that a musician uses a specific musical instrument in their performances |
| case6_weighted | playsMusic | 607 | True | Musician | Genre | indicates that a musician performs music within a specific genre |
| case6_weighted | population | 1 | True | City | Population | indicates that a city has a total population count |
| case6_weighted | populationDensity | 1 | True | City | PopulationDensity | indicates that a city has a specific population density |
| case6_weighted | populationGroup | 58 | True | Nation | EthnicGroup | indicates that a nation is composed of a specific ethnic group |
| case6_weighted | populationMetro | 401 | True | City | Population | indicates that a city has a total metropolitan population count |
| case6_weighted | position | 217 | True | Politician | LegislativeOffice | indicates that a politician holds a legislative office position |
| case6_weighted | postalCode | 296 | True | Village | PostalCode | represents the relationship where a village is linked to a standardized alphanumeric postal code |
| case6_weighted | postalCodeRange | 561 | True | City | PostalCodeRange | represents the relationship where a citys postal codes are grouped within a specific range |
| case6_weighted | postgraduateStudents | 66 | True | University | PostgraduateStudents | indicates that a university has a specific number of students enrolled in postgraduate programs |
| case6_weighted | powerType | 2 | True |  |  |  |
| case6_weighted | precedes | 100 | True | FantasyWork | FantasyWork | indicates that one work of fiction follows another in a chronological order |
| case6_weighted | predecessorWork | 849 | True | Book | Book | indicates that one book came before another in a series |
| case6_weighted | premieredOn | 97 | True | Program | EventDate | indicates that a program was broadcast on a specific event date |
| case6_weighted | prequelOf | 396 | True | Book | Book | represents the relationship where one book is a prequel to another |
| case6_weighted | president | 691 | True | EducationalInstitution | Individual | indicates that an educational institution is led by an individual holding a leadership position |
| case6_weighted | presidentDuringService | 326 | True | Politician | Politician | indicates that a politician served during the presidency of another politician |
| case6_weighted | presidentDuringTenure | 311 | True | Politician | Politician | represents the relationship where a politician serves as president during a specific tenure |
| case6_weighted | presidentServedUnder | 429 | True | Politician | Politician | represents the relationship where a politician served under a specific president |
| case6_weighted | previousChampion | 88 | True | SportsTeam | SportsTeam | indicates that a sports team has previously won a championship |
| case6_weighted | previousChampions | 419 | True | League | SportsClub | represents the relationship where a league has previously been won by a sports club |
| case6_weighted | previousPosition | 914 | True | HistoricalFigure | ProfessionalRole | indicates that a historical figure held a previous professional role |
| case6_weighted | previousRole | 90 | True | Athlete | TeamRole | indicates that an athlete held a specific role in a previous team |
| case6_weighted | previousTeam | 90 | True | Athlete | SportsTeam | indicates that an athlete previously played for a different sports team |
| case6_weighted | previouslyLedBy | 1097 | True | City | Politician | represents the relationship where a city was previously governed by a political leader |
| case6_weighted | produced | 208 | True | AutomotiveCompany | Automobile | indicates that an automotive company manufactures a specific vehicle model |
| case6_weighted | produces | 27 | True | Company | Software | indicates that a company manufactures or develops software products |
| case6_weighted | product | 187 | True | Company | HeatingVentilationAir Conditioning | indicates that a company produces a specific type of product |
| case6_weighted | productionEndYear | 137 | True | Automobile | Year | indicates that an automobile ceased production in a specific year |
| case6_weighted | productionEnded | 855 | True | Automobile | Thing | represents the relationship where an automobile production ends at a particular point in time |
| case6_weighted | productionLocation | 137 | True | Automobile | State | indicates that an automobile is manufactured in a specific state |
| case6_weighted | productionPeriod | 281 | True | Locomotive | ProductionPeriod | indicates that a locomotive was manufactured within a specific time frame |
| case6_weighted | productionStartYear | 60 | True | Automobile | Year | indicates that an automobile begins production in a specific year |
| case6_weighted | propertyOf | 244 | True | ArchitecturalStructure | University | indicates that a university owns the architectural structure |
| case6_weighted | publicationDate | 253 | True | FantasyNovel | PublicationDate | represents the relationship where a fantasy novel has a specific release date |
| case6_weighted | published | 253 | True | Publisher | FantasyNovel | indicates that a publisher releases a fantasy novel into the market |
| case6_weighted | publisher | 100 | True | FantasyWork | Publisher | indicates that a publisher is responsible for the publication of a work of fiction |
| case6_weighted | receivedAward | 53 | True | HistoricalFigure | MilitaryAward | indicates that a historical figure has been awarded a military honor |
| case6_weighted | region | 26 | True | Dessert | GeographicArea | indicates that a dessert is associated with a specific geographic region |
| case6_weighted | relateto | 7 | True | County | County | indicates that two counties are geographically adjacent to each other |
| case6_weighted | relationTo | 459 | True | Book | Book | represents the relationship where one book is related to another book |
| case6_weighted | relationToOther | 688 | True | Actor | Daughter | represents the relationship where an actor is the father of another person |
| case6_weighted | relationTo_Alan_Shepard | 840 | True | EducationalInstitution | Graduation | represents the relationship where an educational institution is associated with an individual completing an educational program |
| case6_weighted | relativePositionTo | 555 | True | County | County | indicates that one county is geographically positioned relative to another county |
| case6_weighted | releaseDate | 172 | True | Book | ReleaseDate | indicates that a book was released on a specific date |
| case6_weighted | represented | 217 | True | Politician | State | indicates that a politician represents a specific state |
| case6_weighted | requires | 860 | True | SweetDish | FoodItem | indicates that a dessert requires a specific food item as an ingredient |
| case6_weighted | requiresIngredient | 1051 | True | SweetFood | BakedGood | indicates that a dessert requires a specific type of baked good as one of its ingredients |
| case6_weighted | retiredOn | 69 | True | HistoricalFigure | Date | indicates that a historical figure retired on a specific date |
| case6_weighted | retirementDate | 615 | True | HistoricalFigure | RetirementDate | indicates that a historical figure retires on a specific date |
| case6_weighted | revenue | 117 | True | Company | Revenue | represents the relationship where a company generates a specific amount of income |
| case6_weighted | role | 332 | True | Citizen | Professional | indicates that a citizen holds a specific professional role |
| case6_weighted | rotationPeriod | 33 | True | Asteroid | RotationPeriod | indicates that an asteroid has a specific rotation period |
| case6_weighted | rotation_period | 103 | True | Planet | Duration | indicates that a planet completes one rotation in a given duration |
| case6_weighted | rotationalPeriod | 109 | True | Asteroid | RotationalPeriod | indicates that an asteroid rotates on its axis in a specific amount of time |
| case6_weighted | runwayLength | 10 | True | Airbase | RunwayLength | indicates that an airbase has a specific runway length |
| case6_weighted | runwayMaterial | 249 | True | Aerodrome | Concrete | represents the relationship where an aerodrome runway is constructed with concrete |
| case6_weighted | runwayName | 45 | True | Airport | RunwayName | indicates that an airport has a unique runway name |
| case6_weighted | runwaySurface | 122 | True | Aerodrome | Concrete | indicates that an aerodrome has a runway surface made of concrete |
| case6_weighted | runwaySurfaceMaterial | 502 | True | Aerodrome | ConstructionMaterial | indicates that an aerodrome has a runway surface made of a specific construction material |
| case6_weighted | runwaySurfaceType | 494 | True |  |  |  |
| case6_weighted | school | 703 | True | HistoricalFigure | EducationalInstitution | indicates that a historical figure attended an educational institution |
| case6_weighted | selectedBy | 11 | True | Individual | GovernmentAgency | indicates that an individual is selected by a governmental agency |
| case6_weighted | selectedYear | 337 | True | HistoricalFigure | SelectionYear | indicates that a historical figure was selected in a specific year |
| case6_weighted | selectionYear | 11 | True | GovernmentAgency | Year | indicates that a governmental agency selects individuals in a specific year |
| case6_weighted | sells | 22 | True | PharmaceuticalCompany | PersonalCareProduct | indicates that a pharmaceutical company offers personal care products |
| case6_weighted | servedAs | 19 | True | DessertFood | Dessert | indicates that a dessert food item is specifically prepared as a sweet course at the end of a meal |
| case6_weighted | servedAt | 485 | True | SweetDish | DessertCourse | indicates that a sweet dish is served as part of a dessert course |
| case6_weighted | servedBy | 1155 | True | Aerodrome | Autodrome | represents the relationship where an aerodrome is managed by an autodrome |
| case6_weighted | servedFor | 569 | True | SweetDish | SweetMeal | indicates that a sweet dish is typically served as a dessert course |
| case6_weighted | serves | 56 | True | Aerodrome | Autodrome | indicates that an aerodrome facilitates the use of another facility |
| case6_weighted | servesAs | 569 | True | Nation | SweetDish | indicates that a nation is associated with a particular sweet dish |
| case6_weighted | serviceBranch | 154 | True | HistoricalFigure | MilitaryBranch | indicates that a historical figure served in a specific military branch |
| case6_weighted | singsIn | 716 | True | Musician | Band | represents the relationship where a musician is a member of a musical group |
| case6_weighted | southeastNeighbor | 501 | True | AdministrativeDivision | AdministrativeDivision | indicates that an administrative division is geographically located to the southeast of another |
| case6_weighted | southeastNeighbour | 165 | True | County | County | indicates that a county is geographically located southeast of another county |
| case6_weighted | southeastOf | 1116 | True | County | County | indicates that one county is geographically located to the southeast of another county |
| case6_weighted | southwestNeighbour | 165 | True | County | County | indicates that a county is geographically located southwest of another county |
| case6_weighted | sportsOffered | 522 | True | EducationalInstitution | RecreationalSport | indicates that an educational institution offers a recreational sport |
| case6_weighted | spouse | 28 | True | Politician | Individual | indicates that a politician is married to an individual |
| case6_weighted | staffCount | 871 | True | University | StaffCount | indicates that a university has a total number of staff members employed |
| case6_weighted | staffMembers | 66 | True | University | StaffMembers | indicates that a university has a specific number of individuals employed by the institution |
| case6_weighted | staffSize | 770 | True | University | StaffSize | indicates that a university has a specific number of staff members |
| case6_weighted | staffTotal | 768 | True | University | StaffTotal | indicates that a university has a total number of staff members |
| case6_weighted | starred | 167 | True | Program | Actor | indicates that a program features a specific actor |
| case6_weighted | starredBy | 867 | True | TelevisionShow | Actor | indicates that a television show features a specific actor |
| case6_weighted | starredIn | 472 | True | Actor | Broadcast | represents the relationship where an actor participates in a broadcast program |
| case6_weighted | starring | 91 | True | TV_series | Individual | indicates that a TV series features individual actors |
| case6_weighted | starringIn | 1133 | True | Actor | TVShow | indicates that an Actor is a key performer in a TVShow |
| case6_weighted | startDate | 997 | True | EducationalFacility | TemporalEntity | indicates that an educational facility was constructed on a specific date |
| case6_weighted | startDateConstruction | 112 | True | Structure | Year | indicates that construction on a building began on a specific year |
| case6_weighted | startDateOfCareer | 523 | True | TranceMusician | Year | indicates that a trance musician begins their career in a specific year |
| case6_weighted | startedPerforming | 20 | True | Musician | Date | indicates that a musician began performing at a specific date |
| case6_weighted | state | 548 | True | AdministrativeDivision | AdministrativeDivision | represents the relationship where an administrative division belongs to a state |
| case6_weighted | status | 146 | True | EducationalInstitution | EducationalStatus | indicates that an educational institution is recognized with a specific designation by a regulatory body |
| case6_weighted | statusGrantedBy | 254 | True | EducationalInstitution | EducationalCouncil | indicates that an educational institution receives a status designation from an educational council |
| case6_weighted | studentCount | 871 | True | University | StudentCount | indicates that a university has a total number of students enrolled |
| case6_weighted | studentCount_Doctoral | 871 | True | University | StudentCount_Doctoral | indicates that a university has a specific number of doctoral students enrolled |
| case6_weighted | studentCount_Postgraduate | 871 | True | University | StudentCount_Postgraduate | indicates that a university has a specific number of postgraduate students enrolled |
| case6_weighted | studentCount_Undergraduate | 871 | True | University | StudentCount_Undergraduate | indicates that a university has a specific number of undergraduate students enrolled |
| case6_weighted | studentType | 871 | True |  |  |  |
| case6_weighted | students | 310 | True | University | StudentCount | indicates that a university has a total number of students |
| case6_weighted | studiesAt | 36 | True | Person | EducationalInstitution | Indicates that a person studies at an educational institution. |
| case6_weighted | succeeded | 353 | True | Politician | Politician | indicates that one politician replaces another in a political leadership role |
| case6_weighted | succeededBy | 912 | True | Politician | Politician | represents the relationship where one politician is succeeded by another |
| case6_weighted | successor | 152 | True | Politician | Politician | represents the relationship where one politician succeeds another in a political role |
| case6_weighted | support | 610 | True | University | StudentPopulation | indicates that a university institution provides support services to a student body |
| case6_weighted | team | 42 | True | Player | Team | indicates that a player competes with a specific team |
| case6_weighted | teamLocation | 700 | True | Athlete | Stadium | indicates that an athletes team is based at a specific stadium |
| case6_weighted | technicalCampusAffiliation | 685 | True | EducationalInstitution | RegulatoryBody | indicates that an educational institution is affiliated with a regulatory body responsible for technical education |
| case6_weighted | technicalCampusStatus | 978 | True | EducationalInstitution | GrantStatus | represents the relationship where an educational institution is granted a specific status by a regulatory body |
| case6_weighted | timeZone | 73 | True | City | Timezone | indicates that a city operates within a specific time zone |
| case6_weighted | timezone | 61 | True | City | StandardTimezone | indicates that a city operates under a specific time zone |
| case6_weighted | toTheSouthEastOf | 107 | True | County | County | indicates that one county is located to the southeast of another county |
| case6_weighted | tookPartIn | 125 | True | Astronaut | SpaceMission | indicates that an astronaut participates in a spaceflight mission |
| case6_weighted | totalArea | 802 | True | Country | Area | indicates that a country has a specific total area |
| case6_weighted | totalNumberOfStudents | 136 | True | University | TotalNumberOfStudents | indicates that a university has a comprehensive student body count |
| case6_weighted | totalStudents | 352 | True | University | TotalStudents | indicates that a university has a total number of enrolled students |
| case6_weighted | type | 7 | True |  |  |  |
| case6_weighted | undergraduateCount | 610 | True | StudentPopulation | UndergraduateCount | represents the relationship where a student population includes a specific count of undergraduate students |
| case6_weighted | undergraduateStudentCount | 136 | True | University | UndergraduateStudentCount | indicates that a university has a specific count of undergraduate students |
| case6_weighted | undergraduateStudentPopulation | 932 | True | University | StudentPopulation | indicates that a university has a specific number of undergraduate students |
| case6_weighted | undergraduateStudents | 956 | True | University | UndergraduateStudents | indicates that a university has a specific number of undergraduate students enrolled |
| case6_weighted | undergraduateTotal | 768 | True | University | UndergraduateTotal | indicates that a university has a specific number of undergraduate students |
| case6_weighted | undergraduates | 1127 | True | EducationalInstitution | Undergraduates | indicates that an educational institution has a count of students enrolled in undergraduate programs |
| case6_weighted | uses | 313 | True | DessertFood | Cheese | indicates that a dessert food item utilizes a specific ingredient |
| case6_weighted | utcOffset | 1 | True | City | UTCOffset | indicates that a city has a UTC offset |
| case6_weighted | wasAMemberOf | 1049 | True | Astronaut | SpaceMission | indicates that an astronaut participates in a specific spaceflight mission |
| case6_weighted | wasCrewMemberOf | 1089 | True | Astronaut | SpaceMission | indicates that an astronaut serves as a crew member on a space mission |
| case6_weighted | wasFoundedBy | 221 | True | BroadcastingCompany | FoundingEntity | indicates that a broadcasting company was founded by a specific founding entity |
| case6_weighted | wasInOfficeWhile | 728 | True | Individual | Presidency | indicates that an individual held a position during a specific presidency |
| case6_weighted | wasMarriedTo | 882 | True | Individual | Individual | indicates that an individual was married to another individual |
| case6_weighted | wasMemberOf | 69 | True | HistoricalFigure | SpaceMission | represents the relationship where a historical figure was part of a space mission |
| case6_weighted | wasOn | 375 | True | MilitaryPerson | SpaceMission | indicates that a military person participated in a space mission |
| case6_weighted | wasPartOf | 639 | True | Astronaut | SpaceMission | indicates that an astronaut participates in a space mission |
| case6_weighted | weight | 46 | True | Individual | Weight | indicates that an individuals weight is measured |
| case6_weighted | westNeighbor | 501 | True | AdministrativeDivision | AdministrativeDivision | indicates that an administrative division is geographically located to the west of another |
| case6_weighted | winLeague | 128 | True | SportsTeam | League | indicates that a sports team has won a league |
| case6_weighted | winLeagueTitle | 498 | True | SportsTeam | ProfessionalLeague | indicates that a sports team has won a league title |
| case6_weighted | winningLeague | 179 | True | SportsClub | League | indicates that a sports club won a league |
| case6_weighted | wonChampionship | 293 | True | SportsTeam | League | indicates that a sports team achieved victory in a league organized by a governing body |
| case6_weighted | wonLeague | 76 | True | SportsTeam | League | indicates that a sports team has won a league championship |
| case6_weighted | wonLeagueChampionship | 189 | True | SportsTeam | Year | indicates that a sports team won a league championship in a specific year |
| case6_weighted | wrote | 351 | True | Author | Book | represents the relationship where an author creates a book |
| case6_weighted | year | 82 | True | League | Year | indicates that a league takes place in a specific year |
| case6_weighted | yearBegunCareer | 595 | True | Musician | Year | indicates that a musician began their musical career in a specific year |
| case6_weighted | yearErected | 247 | True | HistoricalMonument | Year | represents the relationship where a monument is associated with a specific year of erection |
| case6_weighted | yearInLeague | 128 | True | SportsTeam | Year | indicates that a sports team has been in a league for a specific year |
| case6_weighted | yearInPosition | 242 | True | HistoricalFigure | YearInPosition | indicates that a historical figure served in a leadership role for a specific year |
| case6_weighted | yearOfBirth | 909 | True | Individual | Year | indicates that an individual was born in a specific year |
| case6_weighted | yearOfConstruction | 836 | True | Monument | Year | indicates that a monument was constructed in a specific year |
| case6_weighted | yearOfDeath | 909 | True | Individual | Year | indicates that an individual died in a specific year |
| case6_weighted | yearOfGraduation | 557 | True | Historian | Year | indicates that a historian graduated from their educational institution in a specific year |
| case6_weighted | youthClub | 101 | True | Athlete | SportsTeam | indicates that an athlete is a member of the youth team of a sports club |
| case6_weighted | youthFootballClub | 1026 | True | Athlete | YouthFootballClub | indicates that an athlete was initially nurtured by a youth football club |
| case6_weighted | youthSideOf | 162 | True | Athlete | SportsTeam | indicates that an athlete is part of a youth team of a sports team |
| case6_weighted | youthTeam | 192 | True | SportsTeam | Athlete | indicates that a sports team has an affiliated youth athlete |


## First 200 Relation Events

| case | idx | triplet_idx | raw_relation | relation_status | cumulative_relations_after_event |
| --- | --- | --- | --- | --- | --- |
| case1_name_only | 0 | 0 | location | new | 1 |
| case1_name_only | 1 | 0 | isPartOf | new | 2 |
| case1_name_only | 1 | 1 | populationDensity | new | 3 |
| case1_name_only | 1 | 2 | population | new | 4 |
| case1_name_only | 1 | 3 | utcOffset | new | 5 |
| case1_name_only | 1 | 4 | governmentType | new | 6 |
| case1_name_only | 1 | 5 | leaderTitle | new | 7 |
| case1_name_only | 2 | 0 | powerType | new | 8 |
| case1_name_only | 2 | 1 | length | new | 9 |
| case1_name_only | 3 | 0 | architect | new | 10 |
| case1_name_only | 3 | 1 | address | new | 11 |
| case1_name_only | 3 | 2 | currentTenants | new | 12 |
| case1_name_only | 3 | 3 | location | reused | 12 |
| case1_name_only | 3 | 4 | country | new | 13 |
| case1_name_only | 4 | 0 | bornIn | new | 14 |
| case1_name_only | 4 | 1 | diedIn | new | 15 |
| case1_name_only | 4 | 2 | ethnicGroup | new | 16 |
| case1_name_only | 5 | 0 | manager | new | 17 |
| case1_name_only | 5 | 1 | numberOfMembers | new | 18 |
| case1_name_only | 5 | 2 | country | reused | 18 |
| case1_name_only | 6 | 0 | firstAired | new | 19 |
| case1_name_only | 6 | 1 | creator | new | 20 |
| case1_name_only | 6 | 2 | broadcastedBy | new | 21 |
| case1_name_only | 7 | 0 | builtIn | new | 22 |
| case1_name_only | 7 | 1 | location | reused | 22 |
| case1_name_only | 7 | 2 | municipality | new | 23 |
| case1_name_only | 7 | 3 | county | new | 24 |
| case1_name_only | 7 | 4 | type | new | 25 |
| case1_name_only | 7 | 5 | isPartOf | reused | 25 |
| case1_name_only | 7 | 6 | isPartOf | reused | 25 |
| case1_name_only | 7 | 7 | relateto | new | 26 |
| case1_name_only | 8 | 0 | type | reused | 26 |
| case1_name_only | 9 | 0 | owns | new | 27 |
| case1_name_only | 9 | 1 | country | reused | 27 |
| case1_name_only | 9 | 2 | currentTenants | reused | 27 |
| case1_name_only | 9 | 3 | owns | reused | 27 |
| case1_name_only | 10 | 0 | operatedBy | new | 28 |
| case1_name_only | 10 | 1 | runwayLength | new | 29 |
| case1_name_only | 11 | 0 | bornIn | reused | 29 |
| case1_name_only | 11 | 1 | diedIn | reused | 29 |
| case1_name_only | 11 | 2 | nationality | new | 30 |
| case1_name_only | 11 | 3 | selectedBy | new | 31 |
| case1_name_only | 11 | 4 | selectionYear | new | 32 |
| case1_name_only | 12 | 0 | isPartOf | reused | 32 |
| case1_name_only | 13 | 0 | birthPlace | new | 33 |
| case1_name_only | 13 | 1 | birthDate | new | 34 |
| case1_name_only | 13 | 2 | nationality | reused | 34 |
| case1_name_only | 13 | 3 | occupation | new | 35 |
| case1_name_only | 14 | 0 | operatedBy | reused | 35 |
| case1_name_only | 14 | 1 | icaoLocationIdentifier | new | 36 |
| case1_name_only | 15 | 0 | location | reused | 36 |
| case1_name_only | 15 | 1 | operatedBy | reused | 36 |
| case1_name_only | 15 | 2 | altitudeAboveSeaLevel | new | 37 |
| case1_name_only | 15 | 3 | runwayLength | reused | 37 |
| case1_name_only | 16 | 0 | ground | new | 38 |
| case1_name_only | 16 | 1 | numberOfMembers | reused | 38 |
| case1_name_only | 16 | 2 | league | new | 39 |
| case1_name_only | 16 | 3 | country | reused | 39 |
| case1_name_only | 16 | 4 | league | reused | 39 |
| case1_name_only | 16 | 5 | country | reused | 39 |
| case1_name_only | 16 | 6 | champions | new | 40 |
| case1_name_only | 17 | 0 | affiliation | new | 41 |
| case1_name_only | 17 | 1 | country | reused | 41 |
| case1_name_only | 17 | 2 | country | reused | 41 |
| case1_name_only | 19 | 0 | isA | new | 42 |
| case1_name_only | 19 | 1 | foundIn | new | 43 |
| case1_name_only | 19 | 2 | servedAs | new | 44 |
| case1_name_only | 20 | 0 | isA | reused | 44 |
| case1_name_only | 20 | 1 | startedPerforming | new | 45 |
| case1_name_only | 20 | 2 | playedWith | new | 46 |
| case1_name_only | 21 | 0 | broadcastedBy | reused | 46 |
| case1_name_only | 21 | 1 | firstAiredOn | new | 47 |
| case1_name_only | 22 | 0 | foundingDate | new | 48 |
| case1_name_only | 22 | 1 | isA | reused | 48 |
| case1_name_only | 22 | 2 | makes | new | 49 |
| case1_name_only | 22 | 3 | sells | new | 50 |
| case1_name_only | 23 | 0 | country | reused | 50 |
| case1_name_only | 23 | 1 | isPartOf | reused | 50 |
| case1_name_only | 23 | 2 | address | reused | 50 |
| case1_name_only | 23 | 3 | architect | reused | 50 |
| case1_name_only | 24 | 0 | isA | reused | 50 |
| case1_name_only | 24 | 1 | ingredients | new | 51 |
| case1_name_only | 24 | 2 | inhabitant | new | 52 |
| case1_name_only | 24 | 3 | currency | new | 53 |
| case1_name_only | 25 | 0 | dateOfBirth | new | 54 |
| case1_name_only | 25 | 1 | nationality | reused | 54 |
| case1_name_only | 25 | 2 | occupation | reused | 54 |
| case1_name_only | 25 | 3 | mission | new | 55 |
| case1_name_only | 25 | 4 | mission | reused | 55 |
| case1_name_only | 26 | 0 | region | new | 56 |
| case1_name_only | 26 | 1 | servedAs | reused | 56 |
| case1_name_only | 26 | 2 | currency | reused | 56 |
| case1_name_only | 27 | 0 | location | reused | 56 |
| case1_name_only | 27 | 1 | mainProduct | new | 57 |
| case1_name_only | 27 | 2 | produces | new | 58 |
| case1_name_only | 28 | 0 | bornIn | reused | 58 |
| case1_name_only | 28 | 1 | nationality | reused | 58 |
| case1_name_only | 28 | 2 | spouse | new | 59 |
| case1_name_only | 28 | 3 | officeHolder | new | 60 |
| case1_name_only | 28 | 4 | deathPlace | new | 61 |
| case1_name_only | 29 | 0 | foundingDate | reused | 61 |
| case1_name_only | 29 | 1 | country | reused | 61 |
| case1_name_only | 29 | 2 | corporateForm | new | 62 |
| case1_name_only | 29 | 3 | managerTitle | new | 63 |
| case1_name_only | 30 | 0 | bornOn | new | 64 |
| case1_name_only | 30 | 1 | memberOf | new | 65 |
| case1_name_only | 30 | 2 | memberOf | reused | 65 |
| case1_name_only | 31 | 0 | isA | reused | 65 |
| case1_name_only | 31 | 1 | populationMetro | new | 66 |
| case1_name_only | 31 | 2 | populationDensity | reused | 66 |
| case1_name_only | 31 | 3 | governmentType | reused | 66 |
| case1_name_only | 31 | 4 | leaderTitle | reused | 66 |
| case1_name_only | 32 | 0 | firstAired | reused | 66 |
| case1_name_only | 32 | 1 | broadcastedBy | reused | 66 |
| case1_name_only | 33 | 0 | discoveredBy | new | 67 |
| case1_name_only | 33 | 1 | discoveryDate | new | 68 |
| case1_name_only | 33 | 2 | rotationPeriod | new | 69 |
| case1_name_only | 33 | 3 | orbitalPeriod | new | 70 |
| case1_name_only | 33 | 4 | apoapsis | new | 71 |
| case1_name_only | 33 | 5 | absoluteMagnitude | new | 72 |
| case1_name_only | 34 | 0 | bornIn | reused | 72 |
| case1_name_only | 34 | 1 | birthYear | new | 73 |
| case1_name_only | 34 | 2 | deathPlace | reused | 73 |
| case1_name_only | 35 | 0 | nationality | reused | 73 |
| case1_name_only | 35 | 1 | diedIn | reused | 73 |
| case1_name_only | 36 | 0 | studiesAt | new | 74 |
| case1_name_only | 37 | 0 | isPartOf | reused | 74 |
| case1_name_only | 37 | 1 | leaderTitle | reused | 74 |
| case1_name_only | 37 | 2 | populationMetro | reused | 74 |
| case1_name_only | 37 | 3 | populationDensity | reused | 74 |
| case1_name_only | 38 | 0 | currentTenants | reused | 74 |
| case1_name_only | 38 | 1 | address | reused | 74 |
| case1_name_only | 38 | 2 | owner | new | 75 |
| case1_name_only | 38 | 3 | location | reused | 75 |
| case1_name_only | 39 | 0 | isPartOf | reused | 75 |
| case1_name_only | 39 | 1 | firstProducedOn | new | 76 |
| case1_name_only | 39 | 2 | lastProducedOn | new | 77 |
| case1_name_only | 39 | 3 | assemblyLineLocation | new | 78 |
| case1_name_only | 40 | 0 | operator | new | 79 |
| case1_name_only | 40 | 1 | location | reused | 79 |
| case1_name_only | 40 | 2 | runwayName | new | 80 |
| case1_name_only | 40 | 3 | length | reused | 80 |
| case1_name_only | 40 | 4 | location | reused | 80 |
| case1_name_only | 41 | 0 | operatedBy | reused | 80 |
| case1_name_only | 41 | 1 | location | reused | 80 |
| case1_name_only | 41 | 2 | runwayLength | reused | 80 |
| case1_name_only | 41 | 3 | altitudeAboveSeaLevel | reused | 80 |
| case1_name_only | 42 | 0 | team | new | 81 |
| case1_name_only | 42 | 1 | currentTeam | new | 82 |
| case1_name_only | 43 | 0 | location | reused | 82 |
| case1_name_only | 44 | 0 | country | reused | 82 |
| case1_name_only | 44 | 1 | leaderTitle | reused | 82 |
| case1_name_only | 45 | 0 | location | reused | 82 |
| case1_name_only | 45 | 1 | altitudeAboveSeaLevel | reused | 82 |
| case1_name_only | 45 | 2 | operator | reused | 82 |
| case1_name_only | 45 | 3 | location | reused | 82 |
| case1_name_only | 45 | 4 | country | reused | 82 |
| case1_name_only | 45 | 5 | runwayName | reused | 82 |
| case1_name_only | 45 | 6 | runwayLength | reused | 82 |
| case1_name_only | 46 | 0 | dateOfBirth | reused | 82 |
| case1_name_only | 46 | 1 | weight | new | 83 |
| case1_name_only | 47 | 0 | location | reused | 83 |
| case1_name_only | 47 | 1 | country | reused | 83 |
| case1_name_only | 47 | 2 | address | reused | 83 |
| case1_name_only | 47 | 3 | address | reused | 83 |
| case1_name_only | 47 | 4 | constructedBy | new | 84 |
| case1_name_only | 47 | 5 | constructionPeriod | new | 85 |
| case1_name_only | 48 | 0 | established | new | 86 |
| case1_name_only | 48 | 1 | location | reused | 86 |
| case1_name_only | 48 | 2 | has | new | 87 |
| case1_name_only | 48 | 3 | isLocatedIn | new | 88 |
| case1_name_only | 48 | 4 | isCategorizedAs | new | 89 |
| case1_name_only | 48 | 5 | isPartOf | reused | 89 |
| case1_name_only | 49 | 0 | dateOfBirth | reused | 89 |
| case1_name_only | 49 | 1 | bornIn | reused | 89 |
| case1_name_only | 49 | 2 | discoveredBy | reused | 89 |
| case1_name_only | 49 | 3 | orbitalPeriod | reused | 89 |
| case1_name_only | 49 | 4 | periapsis | new | 90 |
| case1_name_only | 50 | 0 | isA | reused | 90 |
| case1_name_only | 50 | 1 | playsInstrument | new | 91 |
| case1_name_only | 50 | 2 | isMemberOf | new | 92 |
| case1_name_only | 51 | 0 | operates | new | 93 |
| case1_name_only | 51 | 1 | isBasedIn | new | 94 |
| case1_name_only | 51 | 2 | runwayLength | reused | 94 |
| case1_name_only | 51 | 3 | altitudeAboveSeaLevel | reused | 94 |
| case1_name_only | 52 | 0 | diedIn | reused | 94 |
| case1_name_only | 52 | 1 | placeOfOrigin | new | 95 |
| case1_name_only | 53 | 0 | bornIn | reused | 95 |
| case1_name_only | 53 | 1 | dateOfBirth | reused | 95 |
| case1_name_only | 53 | 2 | education | new | 96 |
| case1_name_only | 53 | 3 | receivedAward | new | 97 |
| case1_name_only | 54 | 0 | bornIn | reused | 97 |
| case1_name_only | 54 | 1 | ethnicGroup | reused | 97 |
| case1_name_only | 54 | 2 | spouse | reused | 97 |
| case1_name_only | 55 | 0 | location | reused | 97 |
| case1_name_only | 55 | 1 | address | reused | 97 |
| case1_name_only | 56 | 0 | operates | reused | 97 |
| case1_name_only | 56 | 1 | operatedBy | reused | 97 |
| case1_name_only | 56 | 2 | locationElevation | new | 98 |
| case1_name_only | 56 | 3 | runwayLength | reused | 98 |
