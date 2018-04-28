### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal.SizeOf i Marshal.PtrToStructure przeciążenia Podziel kod dynamicznych

|   |   |
|---|---|
|Szczegóły|W programie .NET Framework 4.5.1, dynamiczne wiązanie do metod <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, lub <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (za pomocą programu Windows PowerShell, IronPython lub C# dynamiczne słowo kluczowe, np.) może spowodować <code>MethodInvocationExceptions</code> ponieważ zostały dodane nowe przeciążenia metody który może być niejednoznaczna do aparatów skryptów.|
|Sugestia|Zaktualizuj skryptom wyraźnie wskazuje, które przeładowanie powinien być używany. Może to zazwyczaj wykonywane przez jawne rzutowanie parametrów typu metody jako <xref:System.Type>. Zobacz [to łącze](https://support.microsoft.com/kb/2909958/) dla bardziej szczegółowe informacje i przykłady tego, jak w celu obejścia tego problemu.|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|

