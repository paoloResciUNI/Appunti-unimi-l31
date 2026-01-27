# Integer Overflow 

Lo standard ISOC99 dice che l'itenger overflow causa un comportamento non definito. Per questo quando non è presente un sistema che lo controlla esso non si può controllare. 

I numeri in modulo vanno fatte fino al numero più grande che può essere rappresentato. 

## Integer type conversion 

Usare interi di dimensioni (8bit 16bit) diverse può risultare problematico. I bit possono essere troncati o estesi. 

Questo può causare problemi quando si parla di attacchi 