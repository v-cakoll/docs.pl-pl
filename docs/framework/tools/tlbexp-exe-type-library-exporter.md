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
ms.openlocfilehash: 1d2380ff607836b5dc15e7194b90dd3a53d1d2c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180270"
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (Eksporter biblioteki typów)
Eksporter biblioteki typów generuje bibliotekę typów, która opisuje typy zdefiniowane w zestawie środowiska uruchomieniowego języka wspólnego.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
tlbexp assemblyName [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*Assemblyname*|Zestaw, dla którego ma zostać wyeksportowana biblioteka typów.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/asmpath:** *katalog*|Określa lokalizację do przeszukania pod kątem zestawów. W przypadku użycia tej opcji należy jawnie określić lokalizacje do przeszukiwania pod kątem zestawów, do których się odwoływano, łącznie z bieżącym katalogiem.<br /><br /> Korzystając z opcji **asmpath,** eksporter biblioteki typów nie będzie szukać zestawu w globalnej pamięci podręcznej zestawów (GAC).|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/names:** *nazwa pliku*|Określa wielkość liter nazw w bibliotece typów. Argument *nazwy pliku* jest plikiem tekstowym. Każdy wiersz w pliku określa wielkość liter jednej nazwy w bibliotece typów.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/nazwy staruszka**|Wymusza na Tlbexp.exe eksport uzupełnionych nazw typu, gdy występuje konflikt nazw typu. Należy zauważyć, że było to zachowanie domyślne w wersjach wcześniejszych niż .NET Framework w wersji 2.0.|  
|**/out:** *plik*|Określa nazwę pliku biblioteki typów do wygenerowania. Jeżeli pominięto tę opcję, Tlbexp.exe generuje bibliotekę typów o takiej samej nazwie co zestaw (rzeczywista nazwa zestawu, która niekoniecznie jest taka sama jak nazwa pliku zawierającego zestaw) i rozszerzenie .tlb.|  
|**/cisza:**`warningnumber`|Pomija wyświetlanie określonego ostrzeżenia. Tej opcji nie można używać z **/silent**.|  
|**/silent**|Pomija wyświetlanie komunikatów o sukcesie. Tej opcji nie można używać z **/silence**.|  
|**/tlbreference:** *typlibraryname*|Wymusza na Tlbexp.exe jawne rozwiązanie odwołań do biblioteki typów bez konsultacji z rejestrem. Na przykład jeśli zestaw B odwołuje się do zestawu A, można użyć tej opcji, aby dostarczyć jawne odwołanie do biblioteki typów, zamiast polegać na bibliotece typów określonej w rejestrze. Tlbexp.exe wykonuje sprawdzenie wersji, aby zapewnić zgodność wersji biblioteki typów z wersją zestawu; w przeciwnym wypadku wygeneruje błąd.<br /><br /> Należy zauważyć, że opcja **tlbreference** nadal konsultuje się z rejestrem w przypadkach, gdy <xref:System.Runtime.InteropServices.ComImportAttribute> atrybut jest stosowany do interfejsu, który jest następnie implementowany przez inny typ.|  
|**/tlbrefpath:** *ścieżka*|W pełni kwalifikowana ścieżka do biblioteki typów, do którego się odwoływano.|  
|**/win32**|Podczas kompilowania na komputerze 64-bitowym ta opcja określa, że Tlbexp.exe generuje biblioteki typów 32-bitowych.|  
|**/win64**|Podczas kompilowania na komputerze 32-bitowym ta opcja określa, że program Tlbexp.exe generuje bibliotekę typów 64-bitowych.|  
|**/pełne**|Określa tryb informacji pełnej; wyświetla listę wszystkich zestawów, do których się odwoływano i dla których biblioteka typów musi zostać wygenerowana.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
> [!NOTE]
> W opcjach wiersza polecenia programu Tlbexp.exe nie jest rozróżniana wielkość liter i opcje mogą być podawane w dowolnej kolejności. Wystarczy określić część nazwy opcji umożliwiającą jej jednoznaczną identyfikację. Na przykład **/n** jest odpowiednikiem **/nologo**, i **/o:** *outfile.tlb* jest odpowiednikiem **/out: outfile.tlb** *outfile.tlb*.  
  
## <a name="remarks"></a>Uwagi  
 Tlbexp.exe generuje bibliotekę typów, która zawiera definicje typów zdefiniowanych w zestawie. Aplikacje, takie jak Visual Basic 6.0, mogą użyć wygenerowanej biblioteki typów, aby utworzyć powiązanie z typami .NET zdefiniowanymi w zestawie.  
  
> [!IMPORTANT]
> Nie można użyć Tlbexp.exe do eksportowania plików metadanych (.winmd) systemu Windows. Eksportowanie zestawów środowiska wykonawczego systemu Windows nie jest obsługiwane.  
  
 Cały zespół jest konwertowany na raz. Nie można użyć Tlbexp.exe do generowania informacji o typie dla podzbioru typów zdefiniowanych w zestawie.  
  
 Program Tlbexp.exe nie może używać do tworzenia biblioteki typów z zestawu zaimportowanego przy użyciu [importera biblioteki typów (Tlbimp.exe).](tlbimp-exe-type-library-importer.md) Zamiast tego należy odnieść się do oryginalnej biblioteki typów, która została importowana przy użyciu Tlbimp.exe. Można eksportować bibliotekę typów z zestawu, który odwołuje się do zestawów, które zostały importowane przy użyciu Tlbimp.exe. Zobacz przykłady poniżej.  
  
 Tlbexp.exe umieszcza wygenerowane biblioteki typów w bieżącym katalogu roboczym lub katalogu określonym dla pliku wyjściowego. Pojedynczy zestaw może spowodować wygenerowanie kilku bibliotek typów.  
  
 Tlbexp.exe generuje bibliotekę typów, ale nie rejestruje jej. Jest to w przeciwieństwie do [narzędzia Rejestracja zestawu (Regasm.exe),](regasm-exe-assembly-registration-tool.md)który generuje i rejestruje bibliotekę typów. Aby wygenerować i zarejestrować bibliotekę typów w modelu COM, należy użyć Regasm.exe.  
  
 Jeśli nie określisz `/win32` ani `/win64` opcji, program Tlbexp.exe wygeneruje 32-bitową lub 64-bitową bibliotekę typów odpowiadającą typowi komputera, na którym wykonujesz kompilację (komputer 32-bitowy lub 64-bitowy). Do celów kompilacji krzyżowej można `/win64` użyć tej opcji na komputerze 32-bitowym do wygenerowania biblioteki `/win32` typów 64-bitowych, a na komputerze 64-bitowym można użyć tej opcji do wygenerowania biblioteki typów 32-bitowych. W bibliotekach typu 32-bitowego wartość jest ustawiona <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> na <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>. W bibliotekach typu 64-bitowego wartość jest ustawiona <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> na <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>. Wszystkie przekształcenia typu danych (na przykład typy danych o rozmiarze wskaźnika, takie jak `IntPtr` i `UIntPtr`) są odpowiednio konwertowane.  
  
 Jeśli <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut jest używany do <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> określania wartości `VT_UNKOWN` lub `VT_DISPATCH`, Tlbexp.exe <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> ignoruje wszelkie późniejsze użycie pola. Na przykład w następujących podpisach:  
  
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
  
 Należy zauważyć, że program Tlbexp.exe ignoruje to <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> pole.  
  
 Ponieważ biblioteki typów nie mogą pomieścić wszystkich informacji znajdujących się w zestawach, Tlbexp.exe może odrzucić niektóre dane podczas procesu eksportu. Aby uzyskać wyjaśnienie procesu przekształcania i identyfikacji źródła każdej informacji emitowanych do biblioteki typów, zobacz [Podsumowanie konwersji biblioteki zestawu do tekstu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100)).  
  
 Należy zauważyć, że eksporter biblioteki `VARIANT`typów eksportuje <xref:System.TypedReference> metody, które mają <xref:System.TypedReference> parametry jako , nawet jeśli obiekt nie ma znaczenia w kodzie niezarządzanym. Podczas eksportowania metod, które mają <xref:System.TypedReference> parametry, Programerując biblioteki typów nie wygeneruje ostrzeżenia lub błędu, a niezarządzany kod, który używa wynikowej biblioteki typów, nie będzie działać poprawnie.  
  
 Eksporter biblioteki typów jest obsługiwany w systemie Microsoft Windows 2000 i nowszych.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie generuje bibliotekę typów o takiej samej `myTest.dll`nazwie jak zestaw znaleziony w pliku .  
  
```console  
tlbexp myTest.dll  
```  
  
 Następujące polecenie generuje bibliotekę typów `clipper.tlb`o nazwie .  
  
```console  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 Poniższy przykład ilustruje użycie Tlbexp.exe do eksportowania biblioteki typów z zestawu, który odwołuje się do zestawów importowanych przy użyciu Tlbimp.exe.  
  
 Najpierw użyj Tlbimp.exe, aby `myLib.tlb` zaimportować bibliotekę typów i zapisać ją jako `myLib.dll`.  
  
```console  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 Następujące polecenie używa kompilatora Języka C# do skompilowania `Sample.dll,` odwołań utworzonych `myLib.dll` w poprzednim przykładzie.  
  
```console  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 Następujące polecenie generuje bibliotekę `Sample.dll` typów dla `myLib.dll`tych odwołań .  
  
```console  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.TypeLibExporterFlags>
- [narzędzia](index.md)
- [Regasm.exe (narzędzie rejestracji zestawów)](regasm-exe-assembly-registration-tool.md)
- [Podsumowanie konwersji biblioteki zdań do biblioteki typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))
- [Tlbimp.exe (importer biblioteki typów)](tlbimp-exe-type-library-importer.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
