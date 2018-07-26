### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal.SizeOf i przeciążenia Marshal.PtrToStructure Przerwij kod dynamicznych

|   |   |
|---|---|
|Szczegóły|Począwszy od programu .NET Framework 4.5.1, dynamicznie powiązanie z metodami <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, lub <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (przy użyciu programu Windows PowerShell, IronPython lub C# dynamiczne słowo kluczowe, na przykład) może spowodować <code>MethodInvocationExceptions</code> ponieważ dodano nowe przeciążenia metody te, które mogą być niejednoznaczne do aparatów obsługi skryptów.|
|Sugestia|Zaktualizuj skrypty, aby wyraźnie wskazać przeciążenie, które powinny być używane. Może to zazwyczaj wykonywane przez jawne rzutowanie parametrów typu metody jako <xref:System.Type>. Zobacz [ten link](https://support.microsoft.com/kb/2909958/) uzyskać bardziej szczegółowe informacje i przykłady sposobów w celu obejścia tego problemu.|
|Zakres|Pomocnicza|
|Wersja|4.5.1|
|Typ|Środowisko uruchomieniowe|

