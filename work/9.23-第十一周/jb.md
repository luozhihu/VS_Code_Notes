groovyScript("
def result='';
def params=\"${_1}\".replaceAll('[\\\\[|\\\\]|\\\\s]', '').split(',').toList(); 
for(i = 0; i < params.size(); i++) {
    if(params[i] == '') return result;
    if(i==0) result += '\\n'; 
    result+=' * @param ' + params[i] + ' ' + params[i] + ((i < params.size() - 1) ?  '\\n' : '')
    }; 
    return result
    ", methodParameters())

groovyScript("
def result = '';
def params=\"${_1}\".replaceAll('[\\\\[|\\\\]|\\\\s]', '').split(',').toList();
def maxLen = 0;
for (i = 0; i < params.size(); i++) {
    def paramLength = params[i].length();
    if (maxLen < paramLength) {
        maxLen = paramLength;
    };
};
for (i = 0; i < params.size(); i++) {
    if (params[i] == '') return result;
    if(i==0) result += '\\n'; 
    def paramLength = maxLen - params[i].length() + 1;
    def spaces = '';
    for (j in 1..paramLength) {
        spaces += ' ';
    };
    result+=' * @param ' + params[i] + spaces + params[i] + ((i < params.size() - 1) ?  '\\n' : '');
};
return result
", methodParameters())