<p align="right">
	<b>Naming Convention</b>
</p>
<hr/>

<sub>- Enum should be 'Pascalcase' and be a singular noun. e.g. Day. </sub><br/>
<sub>- Global Variable should be 'Camelcase', mnemonic, and has a prefix like 'g_' e.g. g_logFile. </sub><br/>
<sub>- Subroutine should be 'Camelcase' separated by underscore and perform an action e.g. check_for_errors. </sub><br/>
<sub>- Local Variable in a Subroutine should be 'Camelcase' and a mnemonic e.g. minWidth, maxWidth, minHeight, maxHeight. </sub><br/>
<sub>- Union should be 'Pascalcase' and a noun e.g. String, Chair, Bike, Button, System, FileSystem. </sub><br/>
<sub>- Structure should be 'Pascalcase' and a noun e.g. String, Chair, Bike, Button, System, FileSystem. </sub><br/>
<sub>- Constant in or out of Union/Structure should be 'Uppercase' but separated by underscore ("_") e.g. MIN_WIDTH, MAX_WIDTH, MIN_HEIGHT, MAX_HEIGHT. </sub><br/>
<sub>- Field in Union/Structure should be 'Camelcase' and a mnemonic e.g. minWidth, maxWidth, minHeight, maxHeight. </sub><br/>
<sub>- Record of Structure should be 'Camelcase' and has state nor a behavior as entity then must be more specific than class name e.g. foldingBike, rockingChair. </sub><br/>
