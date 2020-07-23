# ladok3

## class LadokSession

Det h�r �r ett gr�nssnitt f�r att l�sa och skriva resultat
 till ladok 3. Det best�r av:

* \_\_init__         konstruktor som loggar in och h�mtar grunddata
* get_results      returnerar en dictionary med momentnamn och resultat
* save_result      sparar resultat f�r en student som utkast
* get_student_name

### \_\_init__

```python
    #####################################################################
    #
    # init
    #
    # Konstruktorn loggar in p� ladok3 �ver https genom att h�rma en
    # webbl�sare. 
    #
    # username            - ditt loginid t.ex. alba
    # password            - l�senord

    def __init__(self, username, password):
```

### get_results

```python
    #####################################################################
    #
    # get_results
    #
    # person_nr           - personnummer, flera format accepteras
    #                       t.ex. 19461212-1212
    # course_code         - kurskod t.ex. DD1321
    #
    # RETURNERAR en dictionary fr�n ladok med momentnamn, resultat
    #
    # {'LABP': {'date': '2019-01-14', 'grade': 'P', 'status': 'attested'},
    #  'LABD': {'date': '2019-03-23', 'grade': 'E', 'status': 'pending(1)'},
    #  'TEN1': {'date': '2019-03-13', 'grade': 'F', 'status': 'pending(2)'}}
    #
    #  status:  kan ha f�ljande v�rden vilket gissningsvis betyder: 
    #           attested   - attesterad
    #           pending(1) - utkast
    #           pending(2) - klarmarkerad
    #

    def get_results(self, person_nr_raw, course_code):
```

### save_result

```python
    #####################################################################
    #
    # save_result
    #
    # person_nr           - personnummer, flera format accepteras enligt regex:
    #                       (\d\d)?(\d\d)(\d\d\d\d)[+\-]?(\w\w\w\w)
    # course_code         - kurskod t.ex. DD1321
    # course_moment       - ladokmoment/kursbetyg t.ex. TEN1, LAB1, DD1321 (!)
    #                       om labmomententet �r samma som course_code s� s�tts kursbetyg!
    # result_date         - betygsdatum, flera format accepteras enligt regex
    #                       (\d\d)?(\d\d)-?(\d\d)-?(\d\d)
    # grade_code          - det betyg som ska s�ttas
    # grade_scale         - betygsskala t.ex. AF eller PF. M�jliga betygsskalor
    #                       listas i self.__grade_scales. 
    #
    # RETURNERAR True om det g�tt bra, kastar (f�rhoppningsvis) undantag
    #            om det g�r d�ligt. 
    
    def save_result(self, person_nr_raw, course_code, course_moment, result_date_raw, grade_raw, grade_scale):
```

### get_student_name

```python
    #####################################################################
    #
    # get_student_name
    #
    # person_nr           - personnummer, flera format accepteras enligt regex:
    #                       (\d\d)?(\d\d)(\d\d\d\d)[+\-]?(\w\w\w\w)
    #
    # RETURNERAR en dictionary med f�r- och efternamn
    #
    # {"first_name" : 'Anna', "last_name : 'Andersson'}
    #
    
    def get_student_name(self, person_nr_raw):
```

### get_student_data_JSON
```python
    #####################################################################
    #
    # get_student_data_JSON
    #
    # person_nr           - personnummer, flera format accepteras enligt regex:
    #                       (\d\d)?(\d\d)(\d\d\d\d)[+\-]?(\w\w\w\w)
    #
    # RETURNERAR JSON of the request for studentinformation/student
    def get_student_data_JSON(self, person_nr_raw, lang = 'sv'):
```
### logout
```python
    #####################################################################
    #
    # logout
    #                        Terminate the Ladok session
    #
    # RETURNERAR response to the request
    #
    # Example:     status=ladok_session.logout()
    def logout(self):```

### all_grading_scale
```python
    #####################################################################
    #
    # all_grading_scale
    #
    #
    # RETURNERAR en dictionary of the grading scales
    def all_grading_scale(self):
```
### grading_rights
```python
    #####################################################################
    #
    # grading_rights
    #
    #
    # RETURNERAR en dictionary of the grading rights (of the logged in user)
    def grading_rights(self):
```
### change_local
```python
    #####################################################################
    #
    # change_locale
    #
    # lang               - language code 'en' or 'sv', defaults to 'sv'
    #
    # RETURNERAR reponse to the request
    #
    # Example:     status=ladok_session.change_locale('en')
    def change_locale(self, lang = 'sv'):
```
### course_instances_JSON

```python
    #####################################################################
    #
    # course_instances_JSON
    #
    # course_code        - course code, such as "II2202"
    #
    # lang               - language code 'en' or 'sv', defaults to 'sv'
    #
    # RETURNERAR JSON of resultat/kurstillfalle
    #
    # Example: ladok_session.course_instances('II2202', 'en')
    def course_instances(self, course_code, lang = 'sv'):
```
### organization_info_JSON
```python
    #####################################################################
    #
    # organization_info_JSON
    #
    # RETURNERAR JSON of resultat/organisation/utanlankar for the entire institution of the logged in user
    def organization_info(self):
```

### period_info_JSON
```python
    #####################################################################
    #
    # period_info_JSON
    #
    # RETURNERAR JSON of /resultat/grunddata/period
    def period_info(self):
```
### instance_info
```python
    #####################################################################
    #
    # instance_info
    #
    # course_code        - course code, such as "II2202"
    #
    # instance_code      - instance of the course ('TillfallesKod')
    # 
    # lang               - language code 'en' or 'sv', defaults to 'sv'
    #
    # RETURNERAR en dictionary of course instance information
    #
    # Example: info=ladok_session.instance_info('II2202', instance_code, 'en')
    def instance_info(self, course_code, instance_code, lang = 'sv'):
```
### course_instance_JSON
```python
    #####################################################################
    #
    # course_instance_JSON
    #
    # uid                -  uid of c course instance
    #
    # RETURNERAR JSON of resultat/utbildningsinstans/kursinstans
    #
    # Example: kurs=ladok_session.course_instance_JSON(ii['Utbildningsinstans']['Uid']
    def course_instance(self, uid):
```
### participants_JSON
```python
    #####################################################################
    #
    # participants
    #
    # uid                -  uid of c course instance
    #
    # RETURNERAR JSON of participants in a given course instance
    # 
    # Example:         instance_code='50287'
    #                  ii=ladok_session.instance_info('II2202', instance_code, 'en')
    #                  pl=ladok_session.participants(ii['Uid'])
    def participants_JSON(self, uid):
```
### studystructure_student_JSON
```python
    #####################################################################
    #
    # studystructure_student_JSON
    #
    # uid                -  uid of a student
    #
    # RETURNERAR en dictionary of student information
    def studystructure_student_JSON(self, uid):
```

### canvas_ladok3_spreadsheet.py

Purpose: Use the data in a Canvas course room together with the data from Ladok3 to create a spreadsheet of students in the course
and include their Canvas user_id, name, Ladok3 Uid, program_code, program name, etc.


Input: 
```
canvas_ladok3_spreadsheet.py canvas_course_id
```

Output: outputs a file ('users_programs-COURSE_ID.xlsx) containing a spreadsheet of the users information

```
canvas_ladok3_spreadsheet.py 12162
```
### ladok3_course_instance_to_spreadsheet.py

Purpose: Use the data in Ladok3 together with the data from Canvas to create a spreadsheet of students in a course
instance and include their Canvas user_id (or "not in Canvas" if they do not have a Canvas user_id), name, Ladok3 Uid, program_code, program name, etc.

Optionally include their personnumber with the flag -p or --personnumbers 


Input: 
```
ladok3_course_instance_to_spreadsheet.py course_code course_instance
```

Output: outputs a file ('users_programs-instance-COURSE_INSTANCE.xlsx) containing a spreadsheet of the users information

```
# for the P1 instance in 2019 the course instance is 50287
ladok3_course_instance_to_spreadsheet.py II2202 50287
```


