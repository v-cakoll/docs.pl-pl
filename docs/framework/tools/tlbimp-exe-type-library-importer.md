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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f39f793d3d0a2cf815028ccdb49253c46dac2ec4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631311"
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (Importer biblioteki typów)
Importer biblioteki typów konwertuje definicje typów znalezione w bibliotece typów modelu COM do równoważnych definicji w zestawie środowiska uruchomieniowego języka wspólnego. Wyjściem programu Tlbimp.exe jest plik binarny (zestaw) zawierający metadane środowiska wykonawczego dla typów zdefiniowanych w oryginalnej biblioteki typów. Można sprawdzić ten plik za pomocą narzędzi takich jak [Ildasm.exe](ildasm-exe-il-disassembler.md).  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
tlbimp tlbFile [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*tlbFile*|Nazwa dowolnego pliku zawierającego bibliotekę typów modelu COM.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/asmversion:** *numerwersji*|Określa numer wersji zestawu do produkcji. Określ *numerwersji* w formacie *główna.pomocnicza.kompilacja.poprawka*.|  
|**/Company:** `companyinformation`|Dodaje informacje o firmie do wyjściowego zestawu.|  
|**/Copyright:** `copyrightinformation`|Dodaje informacje o prawach autorskich do wyjściowego zestawu. Te informacje mogą być wyświetlane w **właściwości pliku** okno dialogowe dla zestawu.|  
|**/delaysign**|Określa, że Tlbimp.exe ma podpisać wynikowy zestaw silną nazwą przy użyciu opóźnionego podpisywania. Tę opcję należy określić z oboma **/KeyContainer:**, **/KeyFile:**, lub **/publickey:** opcji. Aby uzyskać więcej informacji na temat procesu podpisywania opóźnionego, zobacz [opóźnienie podpisywania zestawu](../app-domains/delay-sign-assembly.md).|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/ KeyContainer:** *containername*|Podpisuje Wynikowy zestaw silną nazwą, używając pary kluczy publiczny/prywatny znalezionej w kontenerze kluczy określonym przez *containername*.|  
|**/ KeyFile:** *nazwy pliku*|Podpisuje Wynikowy zestaw silną nazwą przy użyciu wydawcy oficjalnej publiczny/prywatny pary kluczy w *filename*.|  
|**/ machine:** `machinetype`|Tworzy to zestaw przeznaczony dla określonego typu komputera (procesor). Obsługiwane typy maszyn: x86, x64, Itanium i Agnostic.|  
|**/ NAMESPACE:** *przestrzeni nazw*|Określa przestrzeń nazw, w którym ma zostać wyprodukowany zestaw.|  
|**/noclassmembers**|Zapobiega dodawaniu przez Tlbimp.exe składowych do klasy. Umożliwia to uniknięcie potencjalnych <xref:System.TypeLoadException>.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/ out:** *nazwy pliku*|Określa nazwę wyjściowego pliku zestawu i przestrzeń nazw, w którym mają być zapisywane definicje metadanych. **/Out** opcji nie ma wpływu na przestrzeń nazw zestawu, jeśli biblioteka typów Określa atrybut niestandardowy języka definicji interfejsu (IDL), który jawnie określa przestrzeń nazw zestawu. Jeśli ta opcja nie zostanie określona, Tlbimp.exe zapisuje metadane do pliku o takiej samej nazwie jak rzeczywista biblioteka zdefiniowana w pliku wejściowym i przypisuje mu rozszerzenie dll. Jeśli plik wyjściowy ma taką samą nazwę jak plik wejściowy, narzędzie wygeneruje błąd, aby zapobiec zastąpieniu biblioteki typów.|  
|**/ primary**|Tworzy podstawowy zestaw międzyoperacyjny dla określonej biblioteki typu. Do zestawu są dodawane informacje wskazujące, że wydawca biblioteki typów wyprodukował zestaw. Określając podstawowy zestaw międzyoperacyjny, różnicuje się zestawu wydawcy od innych zestawów utworzonych z biblioteki typów za pomocą Tlbimp.exe. Należy używać tylko **/primary** opcję, jeśli jesteś wydawcą biblioteki typów importowanej za pomocą Tlbimp.exe. Należy pamiętać, że musisz zarejestrować się podstawowy zestaw międzyoperacyjny [silnej nazwy](../app-domains/strong-named-assemblies.md). Aby uzyskać więcej informacji, zobacz [podstawowe zestawy międzyoperacyjne](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).|  
|**/Product:** `productinformation`|Dodaje informacje o produkcie do wyjściowego zestawu. Te informacje mogą być wyświetlane w **właściwości pliku** okno dialogowe dla zestawu.|  
|**/ProductVersion:** `productversioninformation`|Dodaje informacje o wersji produktu do wyjściowego zestawu. Nie ma żadnych ograniczeń dotyczących formatu. Te informacje mogą być wyświetlane w **właściwości pliku** okno dialogowe dla zestawu.|  
|**/PublicKey:** *nazwy pliku*|Określa plik zawierający klucz publiczny używany do podpisywania wynikowego zestawu. Jeśli określisz **/KeyFile:** lub **/KeyContainer:** opcji zamiast **/publickey:**, Tlbimp.exe generuje klucz publiczny z pary kluczy publiczny/prywatny dostarczone z programem **/KeyFile:** lub **/KeyContainer:**. **/Publickey:** opcja obsługuje klucz testowy i opóźnienia podpisywanie scenariuszy. Plik jest w formacie generowanym przez Sn.exe. Aby uzyskać więcej informacji, zobacz **-p** — opcja programu Sn.exe w [narzędzie silnych nazw (Sn.exe)](sn-exe-strong-name-tool.md).|  
|**/ reference:** *nazwy pliku*|Określa plik zestawu używać do rozpoznawania odwołań do typów zdefiniowanych poza bieżącą biblioteką typów. Jeśli nie określisz **/reference** opcji, Tlbimp.exe automatycznie rekursywnie importuje każdą zewnętrzną bibliotekę typów, której typ biblioteki odwołuje się importowana. Jeśli określisz **/reference** opcji, narzędzie próbuje rozpoznać zewnętrzne typy w zestawach, do którego istnieje odwołanie, zanim importuje inne biblioteki typów.|  
|**/silence:** `warningnumber`|Pomija wyświetlanie określonego ostrzeżenia. Tej opcji nie można używać z **/silent**.|  
|**/silent**|Pomija wyświetlanie komunikatów o sukcesie. Tej opcji nie można używać z **/wyciszyć**.|  
|**/strictref**|Nie importuje biblioteki typów, jeśli narzędzie nie może rozpoznać wszystkich odwołania w bieżącym zestawie, zestawach określonych za pomocą **/reference** opcji lub zarejestrowanych podstawowych zestawach międzyoperacyjnych (PIA).|  
|**/strictref:nopia**|Taki sam jak **/strictref**, ale ignoruje zestawy PIA.|  
|**/sysarray**|Określa, że narzędzie ma zaimportować styl modelu COM SafeArray jako zarządzany <xref:System.Array> typu.|  
|**/tlbreference:** *nazwy pliku*|Określa plik biblioteki typów do użycia do rozpoznawania odwołań do biblioteki typu bez konsultacji z rejestrem.<br /><br /> Należy zauważyć, że ta opcja nie będzie ładować niektórych starszych formatów bibliotek typów.  Jednak nadal można ładować starsze formaty bibliotek typów niejawnie za pośrednictwem rejestru lub bieżącego katalogu.|  
|**/trademark:** `trademarkinformation`|Dodaje informacje o znaku towarowym do wyjściowego zestawu. Te informacje mogą być wyświetlane w **właściwości pliku** okno dialogowe dla zestawu.|  
|**/ transform:** *transformname*|Przekształca metadane określone przez *transformname* parametru.<br /><br /> Określ **dispret** dla *transformname* parametr parametrów transformacji [out, retval] metod w interfejsach tylko do wysyłki (dispinterfaces) na wartości zwracane.<br /><br /> Aby uzyskać więcej informacji dotyczących tej opcji, zobacz przykłady w dalszej części tego tematu.|  
|**/ unsafe**|Produkuje interfejsy bez sprawdzania zabezpieczeń platformy .NET Framework. Wywołanie metody, która jest widoczna w ten sposób, może stanowić zagrożenie bezpieczeństwa. Nie należy używać tej opcji, chyba że masz świadomość ryzyka związanego z ujawnieniem takiego kodu.|  
|**/verbose**|Określa tryb pełnej informacji; wyświetla dodatkowe informacje o importowanej bibliotece typów.|  
|**/VariantBoolFieldToBool**|Konwertuje `VARIANT_BOOL` pól w strukturach, aby <xref:System.Boolean>.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
> [!NOTE]
>  W opcjach wiersza polecenia programu Tlbimp.exe nie jest rozróżniana wielkość liter i opcje mogą być podawane w dowolnej kolejności. Wystarczy określić część nazwy opcji umożliwiającą jej jednoznaczną identyfikację. W związku z tym **/n** jest odpowiednikiem **/nologo** i **/ou:** *outfile.tlb* jest odpowiednikiem **/out:**  *outfile.tlb*.  
  
## <a name="remarks"></a>Uwagi  
 Tlbimp.exe za jednym razem wykonuje konwersje na całej biblioteki typów. Nie można użyć narzędzia do generowania informacji o typie dla podzbioru typów zdefiniowanych w obrębie jednej biblioteki typów.  
  
 Często jest użyteczna lub niezbędna można było przypisać [silnych nazw](../app-domains/strong-named-assemblies.md) do zestawów. W związku z tym Tlbimp.exe zawiera opcje umożliwiającą podawanie informacji niezbędnych do generowania zestawów o silnych nazwach. Zarówno **/KeyFile:** i **/KeyContainer:** podpisują zestawy o silnych nazwach. Dlatego logiczne jest podawanie tylko jedną z tych opcji na raz.  
  
 Można określić wiele zestawów odwołań przy użyciu **/reference** opcji wiele razy.  
  
 Identyfikator zasobu można opcjonalnie dołączyć do pliku biblioteki typów podczas importowania biblioteki typów z modułu zawierającego wiele bibliotek typów. Tlbimp.exe jest w stanie zlokalizować ten plik tylko wtedy, gdy znajduje się w bieżącym katalogu lub jeśli określisz pełną ścieżkę. Zobacz przykład dalej w tym temacie.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie generuje zestaw o takiej samej nazwie jak biblioteka typów znaleziona w `myTest.tlb` i z rozszerzeniem dll.  
  
```  
tlbimp myTest.tlb   
```  
  
 Następujące polecenie generuje zestaw o nazwie `myTest.dll`.  
  
```  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Następujące polecenie generuje zestaw o tej samej nazwie co biblioteka typów określona przez `MyModule.dll\1` i z rozszerzeniem dll. `MyModule.dll\1` musi znajdować się w bieżącym katalogu.  
  
```  
tlbimp MyModule.dll\1  
```  
  
 Następujące polecenie generuje zestaw o nazwie `myTestLib.dll` dla biblioteki typów `TestLib.dll`. **/Transform:dispret** opcji przekształca wszelkie [out, retval] Parametry metod dispinterfaces w bibliotece typów na wartości zwracane w bibliotece zarządzanej.  
  
```  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Biblioteka typów `TestLib.dll`, w powyższym przykładzie zawiera metodę dispinterface o nazwie `SomeMethod` która void i ma [out, retval] parametru. Poniższy kod jest podpisem metody biblioteki typu danych wejściowych dla `SomeMethod` w `TestLib.dll`.  
  
```  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 Określanie **/transform:dispret** opcja powoduje, że Tlbimp.exe przekształca `[out, retval]` parametru `SomeMethod` do `bool` zwracają wartość. Poniżej znajduje się sygnatura metody, którą produkuje Tlbimp.exe dla `SomeMethod` w bibliotece zarządzanej `myTestLib.dll` podczas **/transform:dispret** określono opcję.  
  
```csharp  
bool SomeMethod();  
```  
  
 Jeśli używasz Tlbimp.exe do produkcji zarządzanej biblioteki dla `TestLib.dll` bez określania **/transform:dispret**, narzędzie produkuje następujący podpis metody dla `SomeMethod` w bibliotece zarządzanej `myTestLib.dll`.  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Zobacz także
- [Narzędzia](index.md)
- [Tlbexp.exe (eksporter biblioteki typów)](tlbexp-exe-type-library-exporter.md)
- [Importowanie biblioteki typów jako zestawu](../interop/importing-a-type-library-as-an-assembly.md)
- [Biblioteki typów na zestaw konwersja — podsumowanie](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))
- [Ildasm.exe (dezasembler IL)](ildasm-exe-il-disassembler.md)
- [Sn.exe (narzędzie silnych nazw)](sn-exe-strong-name-tool.md)
- [Zestawy o silnych nazwach](../app-domains/strong-named-assemblies.md)
- [Atrybuty importowania bibliotek typów do zestawów międzyoperacyjnych](https://msdn.microsoft.com/library/81e587b8-393f-43e1-9add-c4b05e65cbfd(v=vs.100))
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
