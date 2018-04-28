### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a>Obiekty odbicia nie mogą być przekazywane z kodu zarządzanego do klientów modelu DCOM poza procesem

|   |   |
|---|---|
|Szczegóły|Obiekty odbicia już nie mogą być przekazywane z kodu zarządzanego do klientów modelu DCOM poza procesem. Uwzględnione są następujące:<ul><li><xref:System.Reflection.Assembly?displayProperty=name></li><li><xref:System.Reflection.MemberInfo?displayProperty=name> (i jego typów pochodnych, w tym <xref:System.Reflection.FieldInfo?displayProperty=name>, <xref:System.Reflection.MethodInfo?displayProperty=name>, <xref:System.Type?displayProperty=name>, i <xref:System.Reflection.TypeInfo?displayProperty=name>)</li><li><xref:System.Reflection.MethodBody?displayProperty=name></li><li><xref:System.Reflection.Module?displayProperty=name></li><li><xref:System.Reflection.ParameterInfo?displayProperty=name>.</li></ul>Wywołuje się <code>IMarshal</code> dla obiekt zwracany <code>E_NOINTERFACE</code>.|
|Sugestia|Zaktualizuj kod kierowania do pracy z obiektami z systemem innym niż odbicia|
|Zakres|Pomocnicza|
|Wersja|4.6|
|Typ|Środowisko uruchomieniowe|

