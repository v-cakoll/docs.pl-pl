---
title: "Tlbimp.exe (Importer biblioteki typów)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type libraries [.NET Framework], importing
- importing type library
- Tlbimp.exe
- type definition conversion
- Type Library Importer
- type libraries
- converting type definitions
ms.assetid: ec0a8d63-11b3-4acd-b398-da1e37e97382
caps.latest.revision: "29"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a9774a9811d5c53d44d66fba452098367846bf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="tlbimpexe-type-library-importer"></a>Tlbimp.exe (Importer biblioteki typów)
Importer biblioteki typów konwertuje definicje typów znalezione w bibliotece typów modelu COM do równoważnych definicji w zestawie środowiska uruchomieniowego języka wspólnego. Wyjściem programu Tlbimp.exe jest plik binarny (zestaw) zawierający metadane środowiska wykonawczego dla typów zdefiniowanych w oryginalnej biblioteki typów. Można sprawdzić ten plik przy użyciu narzędzia, takie jak [Ildasm.exe](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
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
|**/ firmy:**`companyinformation`|Dodaje informacje o firmie do wyjściowego zestawu.|  
|**/ copyright:**`copyrightinformation`|Dodaje informacje o prawach autorskich do wyjściowego zestawu. Te informacje mogą być wyświetlane w **właściwości pliku** okno dialogowe dla zestawu.|  
|**/delaysign**|Określa, że Tlbimp.exe ma podpisać wynikowy zestaw silną nazwą przy użyciu opóźnionego podpisywania. Tę opcję należy określić przy użyciu jednej **/KeyContainer:**, **/KeyFile:**, lub **/publickey:** opcji. Aby uzyskać więcej informacji na opóźnione proces podpisywania, zobacz [opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).|  
|**/ Help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/ KeyContainer:** *containername*|Podpisuje wynikowego zestawu z mocną nazwą przy użyciu pary kluczy publiczny/prywatny znaleziony w określone przez kontener kluczy *containername*.|  
|**/ KeyFile:** *filename*|Podpisuje wynikowego zestawu z mocną nazwą za pomocą wydawcy oficjalnego publicznego i prywatnego pary kluczy w *filename*.|  
|**/ maszyny:**`machinetype`|Tworzy to zestaw przeznaczony dla określonego typu komputera (procesor). Obsługiwane typy maszyn: x86, x64, Itanium i Agnostic.|  
|**/ NAMESPACE:** *przestrzeni nazw*|Określa przestrzeń nazw, w którym ma zostać wyprodukowany zestaw.|  
|**/noclassmembers**|Zapobiega dodawaniu przez Tlbimp.exe składowych do klasy. Dzięki temu można uniknąć potencjalne <xref:System.TypeLoadException>.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/ out:** *filename*|Określa nazwę wyjściowego pliku zestawu i przestrzeń nazw, w którym mają być zapisywane definicje metadanych. **/Out** opcji nie ma wpływu na przestrzeń nazw zestawu Jeśli biblioteka typów określa niestandardowy atrybut języka definicji interfejsu (IDL), który jawnie określa zestaw przestrzeni nazw. Jeśli ta opcja nie zostanie określona, Tlbimp.exe zapisuje metadane do pliku o takiej samej nazwie jak rzeczywista biblioteka zdefiniowana w pliku wejściowym i przypisuje mu rozszerzenie dll. Jeśli plik wyjściowy ma taką samą nazwę jak plik wejściowy, narzędzie wygeneruje błąd, aby zapobiec zastąpieniu biblioteki typów.|  
|**/ podstawowego**|Tworzy podstawowy zestaw międzyoperacyjny dla określonej biblioteki typu. Do zestawu są dodawane informacje wskazujące, że wydawca biblioteki typów wyprodukował zestaw. Określając podstawowy zestaw międzyoperacyjny, różnicuje się zestawu wydawcy od innych zestawów utworzonych z biblioteki typów za pomocą Tlbimp.exe. Należy używać tylko **/primary** opcji w przypadku, gdy są wydawcy biblioteki typów, które są importowane z Tlbimp.exe. Należy pamiętać, że możesz zalogować podstawowego zestawu międzyoperacyjnego z [silnej nazwy](../../../docs/framework/app-domains/strong-named-assemblies.md). Aby uzyskać więcej informacji, zobacz [podstawowe zestawy międzyoperacyjne](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080).|  
|**/Product:**`productinformation`|Dodaje informacje o produkcie do wyjściowego zestawu. Te informacje mogą być wyświetlane w **właściwości pliku** okno dialogowe dla zestawu.|  
|**/ProductVersion:**`productversioninformation`|Dodaje informacje o wersji produktu do wyjściowego zestawu. Nie ma żadnych ograniczeń dotyczących formatu. Te informacje mogą być wyświetlane w **właściwości pliku** okno dialogowe dla zestawu.|  
|**/PublicKey:** *filename*|Określa plik zawierający klucz publiczny używany do podpisywania wynikowego zestawu. Jeśli określisz **/KeyFile:** lub **/KeyContainer:** opcję zamiast **/publickey:**, Tlbimp.exe generuje klucz publiczny z pary kluczy publiczny/prywatny dostarczonego z programem **/KeyFile:** lub **/KeyContainer:**. **/Publickey:** obsługuje opcji testowania klucza i opóźnione podpisywanie scenariuszy. Plik jest w formacie generowanym przez Sn.exe. Aby uzyskać więcej informacji, zobacz **-p** opcji Sn.exe w [silnej nazwy narzędzia (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).|  
|**/ reference:** *filename*|Określa plik zestawu używać do rozpoznawania odwołań do typów zdefiniowanych poza bieżącą biblioteką typów. Jeśli nie określisz **/reference** opcję Tlbimp.exe automatycznie rekursywnie importuje wszystkie biblioteki typu zewnętrznego, że typ Biblioteka importowana odwołania. Jeśli określisz **/reference** opcji narzędzia próbuje rozpoznać zewnętrznego typów w przywoływanych zestawach przed importuje innych bibliotek typów.|  
|**/ wyłączeniu:**`warningnumber`|Pomija wyświetlanie określonego ostrzeżenia. Nie można użyć tej opcji z **/silent**.|  
|**/silent**|Pomija wyświetlanie komunikatów o sukcesie. Nie można użyć tej opcji z **/wyłączeniu**.|  
|**/strictref**|Importuj biblioteki typów, jeśli narzędzia nie można rozpoznać wszystkich odwołań w ramach bieżącego zestawu, zestawy określony za pomocą **/reference** opcji lub zarejestrowanych podstawowe zestawy międzyoperacyjne (PIAs).|  
|**/strictref:nopia**|Taki sam jak **/strictref**, ale ignoruje PIAs.|  
|**/sysarray**|Określa narzędzie, aby zaimportować styl COM SafeArray jako zarządzanego <xref:System.Array> typu.|  
|**/tlbreference:** *filename*|Określa plik biblioteki typów do użycia do rozpoznawania odwołań do biblioteki typu bez konsultacji z rejestrem.<br /><br /> Należy zauważyć, że ta opcja nie będzie ładować niektórych starszych formatów bibliotek typów.  Jednak nadal można ładować starsze formaty bibliotek typów niejawnie za pośrednictwem rejestru lub bieżącego katalogu.|  
|**/ znak towarowy:**`trademarkinformation`|Dodaje informacje o znaku towarowym do wyjściowego zestawu. Te informacje mogą być wyświetlane w **właściwości pliku** okno dialogowe dla zestawu.|  
|**/ Przekształcenie:** *transformname*|Przekształca metadanych określony przez *transformname* parametru.<br /><br /> Określ **dispret** dla *transformname* parametr [out, retval]. Przekształcanie parametrów metod tylko do wysyłania interfejsy (dispinterfaces) do wartości zwracanych.<br /><br /> Aby uzyskać więcej informacji dotyczących tej opcji, zobacz przykłady w dalszej części tego tematu.|  
|**/ unsafe**|Produkuje interfejsy bez sprawdzania zabezpieczeń platformy .NET Framework. Wywołanie metody, która jest widoczna w ten sposób, może stanowić zagrożenie bezpieczeństwa. Nie należy używać tej opcji, chyba że masz świadomość ryzyka związanego z ujawnieniem takiego kodu.|  
|**/verbose**|Określa tryb pełnej informacji; wyświetla dodatkowe informacje o importowanej bibliotece typów.|  
|**/ VariantBoolFieldToBool**|Konwertuje `VARIANT_BOOL` pól struktur <xref:System.Boolean>.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
> [!NOTE]
>  W opcjach wiersza polecenia programu Tlbimp.exe nie jest rozróżniana wielkość liter i opcje mogą być podawane w dowolnej kolejności. Wystarczy określić część nazwy opcji umożliwiającą jej jednoznaczną identyfikację. W związku z tym  **/n**  jest odpowiednikiem **/nologo** i **/ou:** *outfile.dll* jest odpowiednikiem   **/out:**  *outfile.dll*.  
  
## <a name="remarks"></a>Uwagi  
 Tlbimp.exe za jednym razem wykonuje konwersje na całej biblioteki typów. Nie można użyć narzędzia do generowania informacji o typie dla podzbioru typów zdefiniowanych w obrębie jednej biblioteki typów.  
  
 Często jest przydatne lub niezbędne można było przypisać [silnych nazw](../../../docs/framework/app-domains/strong-named-assemblies.md) do zestawów. W związku z tym Tlbimp.exe zawiera opcje umożliwiającą podawanie informacji niezbędnych do generowania zestawów o silnych nazwach. Zarówno **/KeyFile:** i **/KeyContainer:** opcje podpisywania zestawy o silnych nazwach. Dlatego logiczne jest podawanie tylko jedną z tych opcji na raz.  
  
 Można określić wiele zestawów odwołań za pomocą **/reference** opcję wiele razy.  
  
 Identyfikator zasobu można opcjonalnie dołączyć do pliku biblioteki typów podczas importowania biblioteki typów z modułu zawierającego wiele bibliotek typów. Tlbimp.exe jest w stanie zlokalizować ten plik tylko wtedy, gdy znajduje się w bieżącym katalogu lub jeśli określisz pełną ścieżkę. Zobacz przykład dalej w tym temacie.  
  
## <a name="examples"></a>Przykłady  
 Polecenie generuje zestaw o tej samej nazwie jako znaleźć biblioteki typów w `myTest.tlb` i z rozszerzeniem dll.  
  
```  
tlbimp myTest.tlb   
```  
  
 Polecenie generuje zestaw o nazwie `myTest.dll`.  
  
```  
tlbimp  myTest.tlb  /out:myTest.dll  
```  
  
 Polecenie generuje zestaw o takiej samej nazwie jak biblioteki typów, określony przez `MyModule.dll\1` i z rozszerzeniem dll. `MyModule.dll\1`musi znajdować się w bieżącym katalogu.  
  
```  
tlbimp MyModule.dll\1  
```  
  
 Polecenie generuje zestaw o nazwie `myTestLib.dll` dla biblioteki typów `TestLib.dll`. **/Transform:dispret** opcji przekształca żadnych [out, retval] parametrów metod dispinterfaces w bibliotece typów do wartości zwracanych w bibliotece zarządzanej.  
  
```  
tlbimp TestLib.dll /transform:dispret /out:myTestLib.dll  
```  
  
 Biblioteki typów `TestLib.dll`, w tym przykładzie obejmuje metodę dispinterface o nazwie `SomeMethod` który zwraca typ void i ma [out, retval] parametru. Następujący kod jest podpis metody biblioteki typ danych wejściowych dla `SomeMethod` w `TestLib.dll`.  
  
```  
void SomeMethod([out, retval] VARIANT_BOOL*);  
```  
  
 Określanie **/transform:dispret** opcja powoduje, że Tlbimp.exe do przekształcania `[out, retval]` parametr `SomeMethod` do `bool` zwracają wartość. Poniżej przedstawiono podpis metody tworzącego Tlbimp.exe dla `SomeMethod` w bibliotece zarządzanej `myTestLib.dll` podczas **/transform:dispret** określono opcję.  
  
```csharp  
bool SomeMethod();  
```  
  
 Jeśli używasz Tlbimp.exe do tworzenia zarządzanej biblioteki dla `TestLib.dll` bez określania **/transform:dispret**, narzędzie tworzy następujące podpis metody dla `SomeMethod` w bibliotece zarządzanej `myTestLib.dll`.  
  
```csharp  
void SomeMethod(out bool x);  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Tlbexp.exe (eksporter biblioteki typów)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 [Importowanie biblioteki typów jako zestawu](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [Biblioteki typów na zestaw konwersja — podsumowanie](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
 [Sn.exe (narzędzie silnych nazw)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [Atrybuty Importowanie biblioteki typów zestawy międzyoperacyjne](http://msdn.microsoft.com/en-us/81e587b8-393f-43e1-9add-c4b05e65cbfd)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
