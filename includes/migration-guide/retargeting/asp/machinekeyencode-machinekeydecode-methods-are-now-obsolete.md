### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>Metody MachineKey.Encode i MachineKey.Decode są teraz przestarzałe

|   |   |
|---|---|
|Szczegóły|Te metody są już nieaktualne. Kompilacja kodu, który wywołuje te metody, powoduje powstanie ostrzeżenia kompilatora.|
|Sugestia|Zalecanych rozwiązań alternatywnych są <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> i <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>. Alternatywnie można pominąć ostrzeżenia kompilacji lub można uniknąć za pomocą starszego kompilatora. Interfejsy API są wciąż obsługiwane.|
|Zakres|Pomocnicza|
|Wersja|4.5|
|Typ|Przekierowania|
|Dotyczy interfejsów API|<ul><li><xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li><li><xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType></li></ul>|

