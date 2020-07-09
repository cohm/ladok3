# ladok3

## class LadokSession

Det h�r �r ett gr�nssnitt f�r att l�sa och skriva resultat
 till ladok 3. Det best�r av:

* \__init__         konstruktor som loggar in och h�mtar grunddata
* get_results      returnerar en dictionary med momentnamn och resultat
* save_result      sparar resultat f�r en student som utkast
* get_student_name

### \__init__

```python
    #####################################################################
    #
    # init
    #
    # username          - ditt loginid t.ex. alba
    # password          - l�senord

    def __init__(self, username, password):
```

### get_results

```python
    #####################################################################
    #
    # get_results
    #
    # person_nr          - personnummer, siffror i str�ngformat
    #            t.ex. 19461212-1212
    # course_code          - kurskod t.ex. DD1321
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
    # person_nr          - personnummer, flera format accepteras enligt regex:
    #                      (\d\d)?(\d\d)(\d\d\d\d)[+\-]?(\w\w\w\w)
    #
    # RETURNERAR en dictionary med f�r- och efternamn
    #
    # {"first_name" : 'Anna', "last_name : 'Andersson'}
    #
    
    def get_student_name(self, person_nr_raw):
```

