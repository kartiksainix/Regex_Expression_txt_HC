# Regex_Expression_txt_HC

import re

TIME = r"(?:\(?\d+\)?\s*(?:hours?|hrs?|days?)|twenty[\s-]?four\s*(?:hours?|hrs?|days?)?|forty[\s-]?eight\s*(?:hours?|hrs?|days?)?|seventy[\s-]?two\s*(?:hours?|hrs?|days?)?|one\s*(?:day|days|hour|hours|hr|hrs)?|two\s*(?:day|days|hour|hours|hr|hrs)?|three\s*(?:day|days|hour|hours|hr|hrs)?)"

pattern = re.compile(rf"""
(?ix)
(?:
    (?:re[\s-]?(?:admi(?:ssion|tted)))\s+to\s+the\s+hospital\s+within\s+{TIME}
  | ms-drg\s+payment.*?(?:pre[\s-]?admi(?:ssion)?).*?same\s+day.*?post[\s-]?discharge.*?within\s+{TIME}\s+of\s+an\s+inpatient\s+(?:admission|discharge)
  | drg\s+payment.*?(?:pre[\s-]?admi(?:ssion)?).*?same\s+day.*?within\s+{TIME}\s+of\s+an\s+inpatient\s+admission.*?readmi(?:ssion|tted).*?within\s+{TIME}
  | drg\s+payment.*?(?:pre[\s-]?admi(?:ssion)?).*?same\s+day.*?within\s+{TIME}\s+of\s+an\s+inpatient\s+admission
  | reimbursement.*?(?:pre[\s-]?admi(?:ssion)?).*?same\s+day.*?emergency\s+room.*?post[\s-]?discharge.*?within\s+{TIME}\s+of\s+an\s+inpatient\s+(?:admission|discharge)
)
""", re.IGNORECASE | re.DOTALL)
