---
title: Tlbexp.exe (Eksporter biblioteki typów)
ms.date: 03/30/2017
helpviewer_keywords:
- exporting type library [.NET Framework]
- exporter tool [.NET Framework]
- Tlbexp.exe
- Type Library Exporter
- type libraries [.NET Framework], exporting
ms.assetid: a487d61b-d166-467b-a7ca-d8b52fbff42d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84ae47b984d6a1a207e6678e30991073ba02a438
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044006"
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (Eksporter biblioteki typów)
Eksporter biblioteki typów generuje bibliotekę typów, która opisuje typy zdefiniowane w zestawie środowiska uruchomieniowego języka wspólnego.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
tlbexp assemblyName [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*assemblyName*|Zestaw, dla którego ma zostać wyeksportowana biblioteka typów.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/asmpath:** *katalog*|Określa lokalizację do przeszukania pod kątem zestawów. W przypadku użycia tej opcji należy jawnie określić lokalizacje do przeszukiwania pod kątem zestawów, do których się odwoływano, łącznie z bieżącym katalogiem.<br /><br /> W przypadku korzystania z opcji **asmpath** Eksporter biblioteki typów nie będzie szukał zestawu w globalnej pamięci podręcznej zestawów (GAC).|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/Names:** *Nazwa pliku*|Określa wielkość liter nazw w bibliotece typów. Argument *filename* jest plikiem tekstowym. Każdy wiersz w pliku określa wielkość liter jednej nazwy w bibliotece typów.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/oldnames**|Wymusza na Tlbexp.exe eksport uzupełnionych nazw typu, gdy występuje konflikt nazw typu. Należy zauważyć, że było to zachowanie domyślne w wersjach wcześniejszych niż .NET Framework w wersji 2.0.|  
|**/out:** *plik*|Określa nazwę pliku biblioteki typów do wygenerowania. Jeżeli pominięto tę opcję, Tlbexp.exe generuje bibliotekę typów o takiej samej nazwie co zestaw (rzeczywista nazwa zestawu, która niekoniecznie jest taka sama jak nazwa pliku zawierającego zestaw) i rozszerzenie .tlb.|  
|**/Silence:** `warningnumber`|Pomija wyświetlanie określonego ostrzeżenia. Tej opcji nie można używać z **/Silent**.|  
|**/silent**|Pomija wyświetlanie komunikatów o sukcesie. Tej opcji nie można używać z **/Silence**.|  
|**/tlbreference:** *typelibraryname*|Wymusza na Tlbexp.exe jawne rozwiązanie odwołań do biblioteki typów bez konsultacji z rejestrem. Na przykład jeśli zestaw B odwołuje się do zestawu A, można użyć tej opcji, aby dostarczyć jawne odwołanie do biblioteki typów, zamiast polegać na bibliotece typów określonej w rejestrze. Tlbexp.exe wykonuje sprawdzenie wersji, aby zapewnić zgodność wersji biblioteki typów z wersją zestawu; w przeciwnym wypadku wygeneruje błąd.<br /><br /> Należy zauważyć, że opcja **tlbreference** nadal sprawdza rejestr w przypadkach, gdy <xref:System.Runtime.InteropServices.ComImportAttribute> atrybut jest stosowany do interfejsu, który jest następnie zaimplementowany przez inny typ.|  
|**/tlbrefpath:** *ścieżka*|W pełni kwalifikowana ścieżka do biblioteki typów, do którego się odwoływano.|  
|**/win32**|Podczas kompilowania na komputerze 64-bitowym ta opcja określa, że Tlbexp.exe generuje biblioteki typów 32-bitowych.|  
|**/Win64**|W przypadku kompilowania na komputerze 32-bitowym, ta opcja określa, że Tlbexp. exe generuje bibliotekę typów 64-bitowych.|  
|**/verbose**|Określa tryb informacji pełnej; wyświetla listę wszystkich zestawów, do których się odwoływano i dla których biblioteka typów musi zostać wygenerowana.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
> [!NOTE]
> W opcjach wiersza polecenia programu Tlbexp.exe nie jest rozróżniana wielkość liter i opcje mogą być podawane w dowolnej kolejności. Wystarczy określić część nazwy opcji umożliwiającą jej jednoznaczną identyfikację. Na przykład **/n** jest równoważne **/nologo**i **/o:** *plik. tlb* jest równoważny z **/out:** *plik. tlb*.  
  
## <a name="remarks"></a>Uwagi  
 Tlbexp.exe generuje bibliotekę typów, która zawiera definicje typów zdefiniowanych w zestawie. Aplikacje, takie jak Visual Basic 6.0, mogą użyć wygenerowanej biblioteki typów, aby utworzyć powiązanie z typami .NET zdefiniowanymi w zestawie.  
  
> [!IMPORTANT]
> Nie można użyć Tlbexp.exe do eksportowania plików metadanych (.winmd) systemu Windows. Eksportowanie zestawów środowiska wykonawczego systemu Windows nie jest obsługiwane.  
  
 Cały zespół jest konwertowany na raz. Nie można użyć Tlbexp.exe do generowania informacji o typie dla podzbioru typów zdefiniowanych w zestawie.  
  
 Nie można użyć Tlbexp. exe do utworzenia biblioteki typów z zestawu, który został zaimportowany przy użyciu [importera biblioteki typów (Tlbimp. exe)](tlbimp-exe-type-library-importer.md). Zamiast tego należy odnieść się do oryginalnej biblioteki typów, która została importowana przy użyciu Tlbimp.exe. Można eksportować bibliotekę typów z zestawu, który odwołuje się do zestawów, które zostały importowane przy użyciu Tlbimp.exe. Zobacz przykłady poniżej.  
  
 Tlbexp.exe umieszcza wygenerowane biblioteki typów w bieżącym katalogu roboczym lub katalogu określonym dla pliku wyjściowego. Pojedynczy zestaw może spowodować wygenerowanie kilku bibliotek typów.  
  
 Tlbexp.exe generuje bibliotekę typów, ale nie rejestruje jej. Jest to w przeciwieństwie do [narzędzia rejestracji zestawu (Regasm. exe)](regasm-exe-assembly-registration-tool.md), które generuje i rejestruje bibliotekę typów. Aby wygenerować i zarejestrować bibliotekę typów w modelu COM, należy użyć Regasm.exe.  
  
 Jeśli nie określisz `/win32` opcji lub `/win64` , program Tlbexp. exe generuje bibliotekę typów 32-bitową lub 64-bitową odpowiadającą typowi komputera, na którym wykonujesz kompilację (komputer 32-bitowy lub 64-bitowy). W celu wykonania wielu kompilacji można użyć `/win64` opcji na komputerze 32-bitowym, aby wygenerować bibliotekę typów 64-bitowej i można `/win32` użyć opcji na komputerze 64-bitowym, aby wygenerować bibliotekę typów 32-bitowego. W 32-bitowych bibliotekach <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> typów wartość jest ustawiana na. <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32> W 64-bitowych bibliotekach <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> typów wartość jest ustawiana na. <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64> Wszystkie przekształcenia typu danych (na przykład typy danych o rozmiarze wskaźnika, takie jak `IntPtr` i `UIntPtr`) są odpowiednio konwertowane.  
  
 Jeśli <xref:System.Runtime.InteropServices.MarshalAsAttribute> używasz atrybutu, aby `VT_UNKOWN` <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> określić wartość lub `VT_DISPATCH`, Tlbexp. exe ignoruje wszelkie kolejne użycie <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> pola. Na przykład w następujących podpisach:  
  
```csharp
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_UNKNOWN, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructUnkSafe(){return null;}  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_DISPATCH, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructDispSafe(){return null;}  
```  
  
 generowana jest następująca biblioteka typów:  
  
```cpp 
[id(0x60020004)]  
HRESULT StructUnkSafe([out, retval] SAFEARRAY(IUnknown*)* pRetVal);  
[id(0x60020005)]  
HRESULT StructDispSafe([out, retval] SAFEARRAY(IDispatch*)* pRetVal);  
```  
  
 Należy zauważyć, że Tlbexp. exe <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> ignoruje pole.  
  
 Ponieważ biblioteki typów nie mogą pomieścić wszystkich informacji znajdujących się w zestawach, Tlbexp.exe może odrzucić niektóre dane podczas procesu eksportu. Aby uzyskać informacje na temat procesu transformacji i identyfikacji źródła informacji emitowanych do biblioteki typów, zobacz [Podsumowanie konwersji zestawu na bibliotekę typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100)).  
  
 Należy zauważyć, że Eksporter biblioteki typów eksportuje metody <xref:System.TypedReference> , które `VARIANT`mają parametry AS, <xref:System.TypedReference> nawet jeśli obiekt nie ma znaczenia w kodzie niezarządzanym. Podczas eksportowania metod, które mają <xref:System.TypedReference> parametry, Eksporter biblioteki typów nie będzie generował ostrzeżenia ani błędu i niezarządzany kod, który używa biblioteki typów, nie będzie działać prawidłowo.  
  
 Eksporter biblioteki typów jest obsługiwany w systemie Microsoft Windows 2000 i nowszych.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie generuje bibliotekę typów o takiej samej nazwie jak zestaw znaleziony w `myTest.dll`.  
  
```console  
tlbexp myTest.dll  
```  
  
 Następujące polecenie generuje bibliotekę typów o nazwie `clipper.tlb`.  
  
```console  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 Poniższy przykład ilustruje użycie Tlbexp.exe do eksportowania biblioteki typów z zestawu, który odwołuje się do zestawów importowanych przy użyciu Tlbimp.exe.  
  
 Najpierw należy użyć Tlbimp. exe do zaimportowania `myLib.tlb` biblioteki typów i zapisania `myLib.dll`jej jako.  
  
```console  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 Następujące polecenie używa C# kompilatora do kompilowania `Sample.dll,` odwołań `myLib.dll` utworzonych w poprzednim przykładzie.  
  
```console  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 Następujące polecenie generuje bibliotekę typów dla `Sample.dll` odwołań. `myLib.dll`  
  
```console  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.TypeLibExporterFlags>
- [Narzędzia](index.md)
- [Regasm.exe (narzędzie rejestracji zestawów)](regasm-exe-assembly-registration-tool.md)
- [Podsumowanie konwersji zestawu na bibliotekę typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))
- [Tlbimp.exe (importer biblioteki typów)](tlbimp-exe-type-library-importer.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
