---
title: Tlbimp.exe (Importer biblioteki typów)
ms.date: 03/30/2017
helpviewer_keywords:
- type libraries [.NET Framework], importing
- importing type library
- Tlbimp.exe
- type definition conversion
- Type Library Importer
- type libraries
- converting type definitions
ms.assetid: ec0a8d63-11b3-4acd-b398-da1e37e97382
ms.openlocfilehash: d942378888b06049022188c75456f438d4b187e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180247"
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (Importer biblioteki typów)
Importer biblioteki typów konwertuje definicje typów znalezione w bibliotece typów modelu COM do równoważnych definicji w zestawie środowiska uruchomieniowego języka wspólnego. Wyjściem programu Tlbimp.exe jest plik binarny (zestaw) zawierający metadane środowiska wykonawczego dla typów zdefiniowanych w oryginalnej biblioteki typów. Można sprawdzić ten plik za pomocą narzędzi, takich jak [Ildasm.exe](ildasm-exe-il-disassembler.md).  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
tlbimp tlbFile [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*tlbFile (plik)*|Nazwa dowolnego pliku zawierającego bibliotekę typów modelu COM.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/asmversion:** *numer wersji*|Określa numer wersji zestawu do produkcji. Określ *numer wersji* w formacie *major.minor.build.revision*.|  
|**/firma:**`companyinformation`|Dodaje informacje o firmie do wyjściowego zestawu.|  
|**/copyright:**`copyrightinformation`|Dodaje informacje o prawach autorskich do wyjściowego zestawu. Te informacje można wyświetlić w oknie dialogowym **Właściwości pliku** dla złożenia.|  
|**/delaysign (znak opóźnienia)**|Określa, że Tlbimp.exe ma podpisać wynikowy zestaw silną nazwą przy użyciu opóźnionego podpisywania. Tę opcję należy określić za pomocą opcji **/keycontainer:**, **/keyfile:** lub **/publickey:** . Aby uzyskać więcej informacji na temat procesu opóźnionego podpisywania, zobacz [Opóźnienie podpisania zestawu](../../standard/assembly/delay-sign.md).|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/keycontainer:** *nazwa kontenera*|Podpisuje wynikowy zestaw o silnej nazwie przy użyciu pary kluczy publicznych/prywatnych znalezionych w kontenerze klucza określonym przez *containername*.|  
|**/keyfile:** *nazwa pliku*|Podpisuje wynikowy zestaw o silnej nazwie przy użyciu oficjalnej pary kluczy publicznych/prywatnych wydawcy znalezionej w *nazwie pliku*.|  
|**/maszyna:**`machinetype`|Tworzy to zestaw przeznaczony dla określonego typu komputera (procesor). Obsługiwane typy maszyn: x86, x64, Itanium i Agnostic.|  
|**/obszar nazw:** *obszar nazw*|Określa przestrzeń nazw, w którym ma zostać wyprodukowany zestaw.|  
|**/noclassmembers**|Zapobiega dodawaniu przez Tlbimp.exe składowych do klasy. Pozwala to uniknąć <xref:System.TypeLoadException>potencjalnego .|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/out:** *nazwa pliku*|Określa nazwę wyjściowego pliku zestawu i przestrzeń nazw, w którym mają być zapisywane definicje metadanych. Opcja **/out** nie ma wpływu na obszar nazw zestawu, jeśli biblioteka typów określa atrybut niestandardowy języka IDL (Interface Definition Language), który jawnie steruje przestrzenią nazw zestawu. Jeśli ta opcja nie zostanie określona, Tlbimp.exe zapisuje metadane do pliku o takiej samej nazwie jak rzeczywista biblioteka zdefiniowana w pliku wejściowym i przypisuje mu rozszerzenie dll. Jeśli plik wyjściowy ma taką samą nazwę jak plik wejściowy, narzędzie wygeneruje błąd, aby zapobiec zastąpieniu biblioteki typów.|  
|**/podstawowych**|Tworzy podstawowy zestaw międzyoperacyjny dla określonej biblioteki typu. Do zestawu są dodawane informacje wskazujące, że wydawca biblioteki typów wyprodukował zestaw. Określając podstawowy zestaw międzyoperacyjny, różnicuje się zestawu wydawcy od innych zestawów utworzonych z biblioteki typów za pomocą Tlbimp.exe. Opcji **/primary** należy używać tylko wtedy, gdy jesteś wydawcą biblioteki typów importowanej z programem Tlbimp.exe. Należy zauważyć, że należy podpisać podstawowy zestaw interop o [silnej nazwie](../../standard/assembly/strong-named.md). Aby uzyskać więcej informacji, zobacz [Podstawowe zestawy interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).|  
|**/produkt:**`productinformation`|Dodaje informacje o produkcie do wyjściowego zestawu. Te informacje można wyświetlić w oknie dialogowym **Właściwości pliku** dla złożenia.|  
|**/productversion:**`productversioninformation`|Dodaje informacje o wersji produktu do wyjściowego zestawu. Nie ma żadnych ograniczeń dotyczących formatu. Te informacje można wyświetlić w oknie dialogowym **Właściwości pliku** dla złożenia.|  
|**/publickey:** *nazwa pliku*|Określa plik zawierający klucz publiczny używany do podpisywania wynikowego zestawu. Jeśli określisz **/keyfile:** lub **/keycontainer:** opcja zamiast **/publickey:**, Tlbimp.exe generuje klucz publiczny z pary klucza publicznego/prywatnego dostarczanej z **/keyfile:** lub **/keycontainer:**. Opcja **/publickey:** obsługuje scenariusze klucza testowego i opóźniania podpisywania. Plik jest w formacie generowanym przez Sn.exe. Aby uzyskać więcej informacji, zobacz opcję **-p** sn.exe w [narzędziu Silnej nazwy (Sn.exe)](sn-exe-strong-name-tool.md).|  
|**/reference:** *nazwa pliku*|Określa plik zestawu używać do rozpoznawania odwołań do typów zdefiniowanych poza bieżącą biblioteką typów. Jeśli opcja **/reference** nie zostanie określona, program Tlbimp.exe automatycznie cyklicznie importuje dowolną bibliotekę typów zewnętrznych, do której odwołuje się importowana biblioteka typów. Jeśli określisz **/reference** opcja, narzędzie próbuje rozpoznać typy zewnętrzne w zestawach, do których istnieje odwołanie, zanim zaimportuje inne biblioteki typów.|  
|**/cisza:**`warningnumber`|Pomija wyświetlanie określonego ostrzeżenia. Tej opcji nie można używać z **/silent**.|  
|**/silent**|Pomija wyświetlanie komunikatów o sukcesie. Tej opcji nie można używać z **/silence**.|  
|**/strictref**|Nie importuje biblioteki typów, jeśli narzędzie nie może rozpoznać wszystkich odwołań w bieżącym zestawie, zestawów określonych za pomocą opcji **/reference** lub zarejestrowanych podstawowych zestawów międzyoperacyjnych (PIA).|  
|**/strictref:nopia**|Tak samo jak **/strictref**, ale ignoruje pias.|  
|**/sysarray**|Określa narzędzie do importowania safearray w stylu <xref:System.Array> COM jako typu zarządzanego.|  
|**/tlbreference:** *nazwa pliku*|Określa plik biblioteki typów do użycia do rozpoznawania odwołań do biblioteki typu bez konsultacji z rejestrem.<br /><br /> Należy zauważyć, że ta opcja nie będzie ładować niektórych starszych formatów bibliotek typów.  Jednak nadal można ładować starsze formaty bibliotek typów niejawnie za pośrednictwem rejestru lub bieżącego katalogu.|  
|**/znak towarowy:**`trademarkinformation`|Dodaje informacje o znaku towarowym do wyjściowego zestawu. Te informacje można wyświetlić w oknie dialogowym **Właściwości pliku** dla złożenia.|  
|**/transform:** *transformname*|Przekształca metadane określone przez parametr *transformname.*<br /><br /> Określ **dispret** dla *transformname* parametr przekształcenia [out, retval] parametrów metod na interfejsach tylko do wysyłki (dispinterfaces) do wartości zwracanych.<br /><br /> Aby uzyskać więcej informacji dotyczących tej opcji, zobacz przykłady w dalszej części tego tematu.|  
|**/niebezpieczne**|Produkuje interfejsy bez sprawdzania zabezpieczeń platformy .NET Framework. Wywołanie metody, która jest widoczna w ten sposób, może stanowić zagrożenie bezpieczeństwa. Nie należy używać tej opcji, chyba że masz świadomość ryzyka związanego z ujawnieniem takiego kodu.|  
|**/pełne**|Określa tryb pełnej informacji; wyświetla dodatkowe informacje o importowanej bibliotece typów.|  
|**/VariantBoolFieldToBool**|Konwertuje `VARIANT_BOOL` pola w <xref:System.Boolean>strukturach na .|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
> [!NOTE]
> W opcjach wiersza polecenia programu Tlbimp.exe nie jest rozróżniana wielkość liter i opcje mogą być podawane w dowolnej kolejności. Wystarczy określić część nazwy opcji umożliwiającą jej jednoznaczną identyfikację. W związku z tym **/n** jest odpowiednikiem **/nologo** i **/ou:** *outfile.dll* jest odpowiednikiem **/out:** *outfile.dll*.  
  
## <a name="remarks"></a>Uwagi  
 Tlbimp.exe za jednym razem wykonuje konwersje na całej biblioteki typów. Nie można użyć narzędzia do generowania informacji o typie dla podzbioru typów zdefiniowanych w obrębie jednej biblioteki typów.  
  
 Często jest to przydatne lub konieczne, aby móc przypisać [silne nazwy](../../standard/assembly/strong-named.md) do zestawów. W związku z tym Tlbimp.exe zawiera opcje umożliwiającą podawanie informacji niezbędnych do generowania zestawów o silnych nazwach. Oba **/keyfile:** i **/keycontainer:** opcje podpisują zestawy z silnymi nazwami. Dlatego logiczne jest podawanie tylko jedną z tych opcji na raz.  
  
 Wiele zestawów odwołań można określić przy użyciu opcji **/reference** wiele razy.

 Ze względu na sposób, w jaki Tlbimp.exe generuje zestawy, nie jest możliwe `mscorlib` ponowne kierowanie zestawu do innej wersji. Na przykład jeśli chcesz wygenerować zestaw, który jest przeznaczony dla platformy .NET Framework 2.0, Tlbimp.exe dostarczane z .NET Framework 2.0/3.0/3.5 SDK musi być używany. Aby kierować .NET Framework 4.x, Tlbimp.exe dostarczane z .NET Framework 4.x SDK powinny być używane.

 Identyfikator zasobu można opcjonalnie dołączyć do pliku biblioteki typów podczas importowania biblioteki typów z modułu zawierającego wiele bibliotek typów. Tlbimp.exe jest w stanie zlokalizować ten plik tylko wtedy, gdy znajduje się w bieżącym katalogu lub jeśli określisz pełną ścieżkę. Zobacz przykład dalej w tym temacie.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie generuje zestaw o takiej samej nazwie `myTest.tlb` jak biblioteka typów znajdująca się w i z rozszerzeniem .dll.  
  
```console  
tlbimp myTest.tlb
```  
  
 Następujące polecenie generuje zestaw o `myTest.dll`nazwie .  
  
```console  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Następujące polecenie generuje zestaw o takiej samej nazwie `MyModule.dll\1` jak biblioteka typów określona przez rozszerzenie .dll i z rozszerzeniem .dll. `MyModule.dll\1`musi znajdować się w bieżącym katalogu.  
  
```console  
tlbimp MyModule.dll\1  
```  
  
 Następujące polecenie generuje zestaw o `myTestLib.dll` nazwie biblioteki `TestLib.dll`typów . Opcja **/transform:dispret** przekształca wszelkie parametry [out, retval] metod na dispinterfaces w bibliotece typów w wartości zwracane w bibliotece zarządzanej.  
  
```console  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Biblioteka `TestLib.dll`typów , w poprzednim przykładzie, zawiera metodę `SomeMethod` dispinterface o nazwie, która zwraca void i ma parametr [out, retval]. Poniższy kod jest podpisem metody `SomeMethod` `TestLib.dll`biblioteki typów wejściowych w pliku .  
  
```cpp  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 Określenie **opcji /transform:dispret** powoduje, że Tlbimp.exe `SomeMethod` przekształca `bool` `[out, retval]` parametr w wartość zwracaną. Poniżej przedstawiono podpis metody, który Tlbimp.exe produkuje dla `SomeMethod` w bibliotece `myTestLib.dll` zarządzanej, gdy opcja **/transform:dispret** jest określona.  
  
```csharp  
bool SomeMethod();  
```  
  
 Jeśli tlbimp.exe używasz do tworzenia `TestLib.dll` biblioteki zarządzanej bez określania **/transform:dispret,** `SomeMethod` narzędzie tworzy `myTestLib.dll`następujący podpis metody w bibliotece zarządzanej .  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Tlbexp.exe (Eksporter biblioteki typów)](tlbexp-exe-type-library-exporter.md)
- [Importowanie biblioteki typów jako zestawu](../interop/importing-a-type-library-as-an-assembly.md)
- [Podsumowanie konwersji biblioteki typów na podsumowanie konwersji zestawu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Ildasm.exe (dezasembler IL)](ildasm-exe-il-disassembler.md)
- [Sn.exe (Narzędzie silnych nazw)](sn-exe-strong-name-tool.md)
- [Zestawy o silnych nazwach](../../standard/assembly/strong-named.md)
- [Atrybuty importowania bibliotek typów do zestawów interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/y6a7ak23(v=vs.100))
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
