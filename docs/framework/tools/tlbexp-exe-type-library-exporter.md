---
title: "Tlbexp.exe (Eksporter biblioteki typów)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting type library [.NET Framework]
- exporter tool [.NET Framework]
- Tlbexp.exe
- Type Library Exporter
- type libraries [.NET Framework], exporting
ms.assetid: a487d61b-d166-467b-a7ca-d8b52fbff42d
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47710b81de79a9dfbb6bddd39035be2986350b0e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (Eksporter biblioteki typów)
Eksporter biblioteki typów generuje bibliotekę typów, która opisuje typy zdefiniowane w zestawie środowiska uruchomieniowego języka wspólnego.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
tlbexp assemblyName [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*assemblyName*|Zestaw, dla którego ma zostać wyeksportowana biblioteka typów.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ asmpath:** *katalogu*|Określa lokalizację do przeszukania pod kątem zestawów. W przypadku użycia tej opcji należy jawnie określić lokalizacje do przeszukiwania pod kątem zestawów, do których się odwoływano, łącznie z bieżącym katalogiem.<br /><br /> Jeśli używasz **asmpath** opcji Eksporter biblioteki typów nie będzie szukać zestawu w globalnej pamięci podręcznej zestawów (GAC).|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/ nazwy:** *filename*|Określa wielkość liter nazw w bibliotece typów. *Filename* argument jest plikiem tekstowym. Każdy wiersz w pliku określa wielkość liter jednej nazwy w bibliotece typów.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/oldnames**|Wymusza na Tlbexp.exe eksport uzupełnionych nazw typu, gdy występuje konflikt nazw typu. Należy zauważyć, że było to zachowanie domyślne w wersjach wcześniejszych niż .NET Framework w wersji 2.0.|  
|**/ out:** *pliku*|Określa nazwę pliku biblioteki typów do wygenerowania. Jeżeli pominięto tę opcję, Tlbexp.exe generuje bibliotekę typów o takiej samej nazwie co zestaw (rzeczywista nazwa zestawu, która niekoniecznie jest taka sama jak nazwa pliku zawierającego zestaw) i rozszerzenie .tlb.|  
|**/ wyłączeniu:**`warningnumber`|Pomija wyświetlanie określonego ostrzeżenia. Nie można użyć tej opcji z **/silent**.|  
|**/silent**|Pomija wyświetlanie komunikatów o sukcesie. Nie można użyć tej opcji z **/wyłączeniu**.|  
|**/tlbreference:** *typelibraryname*|Wymusza na Tlbexp.exe jawne rozwiązanie odwołań do biblioteki typów bez konsultacji z rejestrem. Na przykład jeśli zestaw B odwołuje się do zestawu A, można użyć tej opcji, aby dostarczyć jawne odwołanie do biblioteki typów, zamiast polegać na bibliotece typów określonej w rejestrze. Tlbexp.exe wykonuje sprawdzenie wersji, aby zapewnić zgodność wersji biblioteki typów z wersją zestawu; w przeciwnym wypadku wygeneruje błąd.<br /><br /> Należy pamiętać, że **tlbreference** opcji nadal sprawdza rejestru w przypadkach, gdy <xref:System.Runtime.InteropServices.ComImportAttribute> atrybut jest stosowany do interfejsu, który następnie jest implementowane za pomocą innego typu.|  
|**/tlbrefpath:** *ścieżki*|W pełni kwalifikowana ścieżka do biblioteki typów, do którego się odwoływano.|  
|**/win32**|Podczas kompilowania na komputerze 64-bitowym ta opcja określa, że Tlbexp.exe generuje biblioteki typów 32-bitowych.|  
|**/Win64**|W przypadku kompilowania kodu na komputerze 32-bitowym, ta opcja określa, że Tlbexp.exe generuje biblioteki typów 64-bitowych.|  
|**/verbose**|Określa tryb informacji pełnej; wyświetla listę wszystkich zestawów, do których się odwoływano i dla których biblioteka typów musi zostać wygenerowana.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
> [!NOTE]
>  W opcjach wiersza polecenia programu Tlbexp.exe nie jest rozróżniana wielkość liter i opcje mogą być podawane w dowolnej kolejności. Wystarczy określić część nazwy opcji umożliwiającą jej jednoznaczną identyfikację. Na przykład  **/n**  jest odpowiednikiem **/nologo**, i **/o:** *outfile.tlb* jest odpowiednikiem   **/out:**  *outfile.tlb*.  
  
## <a name="remarks"></a>Uwagi  
 Tlbexp.exe generuje bibliotekę typów, która zawiera definicje typów zdefiniowanych w zestawie. Aplikacje, takie jak Visual Basic 6.0, mogą użyć wygenerowanej biblioteki typów, aby utworzyć powiązanie z typami .NET zdefiniowanymi w zestawie.  
  
> [!IMPORTANT]
>  Nie można użyć Tlbexp.exe do eksportowania plików metadanych (.winmd) systemu Windows. Eksportowanie zestawów środowiska wykonawczego systemu Windows nie jest obsługiwane.  
  
 Cały zespół jest konwertowany na raz. Nie można użyć Tlbexp.exe do generowania informacji o typie dla podzbioru typów zdefiniowanych w zestawie.  
  
 Nie można utworzyć bibliotekę typów z zestawu, który został zaimportowany za pomocą za pomocą Tlbexp.exe [Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Zamiast tego należy odnieść się do oryginalnej biblioteki typów, która została importowana przy użyciu Tlbimp.exe. Można eksportować bibliotekę typów z zestawu, który odwołuje się do zestawów, które zostały importowane przy użyciu Tlbimp.exe. Zobacz przykłady poniżej.  
  
 Tlbexp.exe umieszcza wygenerowane biblioteki typów w bieżącym katalogu roboczym lub katalogu określonym dla pliku wyjściowego. Pojedynczy zestaw może spowodować wygenerowanie kilku bibliotek typów.  
  
 Tlbexp.exe generuje bibliotekę typów, ale nie rejestruje jej. Jest to contrast do [narzędzie do rejestrowania zestawów (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md), który zarówno generuje i rejestruje biblioteki typów. Aby wygenerować i zarejestrować bibliotekę typów w modelu COM, należy użyć Regasm.exe.  
  
 Jeśli nie określisz albo `/win32` lub `/win64` opcji Tlbexp.exe generuje biblioteki typów 32-bitowy lub 64-bitowych umożliwiająca typ komputera, na którym działają kompilacji (32-bitowy lub 64-bitowy komputer). Dla celów między kompilacji, możesz użyć `/win64` opcję na komputerze 32-bitowym, aby wygenerować biblioteki typów 64-bitowe i można użyć `/win32` opcję na komputerze 64-bitowym, aby wygenerować biblioteki typów 32-bitowych. W bibliotekach 32-bitowego typu <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> ma wartość <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>. W przypadku 64-bitowego typu bibliotek <xref:System.Runtime.InteropServices.ComTypes.SYSKIND> ma wartość <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>. Wszystkie dane typu przekształcenia (na przykład typy danych o rozmiarze wskaźnika takich jak `IntPtr` i `UIntPtr`) są konwertowane odpowiednio.  
  
 Jeśli używasz <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu, aby określić <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> wartość `VT_UNKOWN` lub `VT_DISPATCH`, Tlbexp.exe ignoruje wszystkie kolejne stosowania <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> pola. Na przykład w następujących podpisach:  
  
```  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_UNKNOWN, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructUnkSafe(){return null;}  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_DISPATCH, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructDispSafe(){return null;}  
```  
  
 generowana jest następująca biblioteka typów:  
  
```  
[id(0x60020004)]  
HRESULT StructUnkSafe([out, retval] SAFEARRAY(IUnknown*)* pRetVal);  
[id(0x60020005)]  
HRESULT StructDispSafe([out, retval] SAFEARRAY(IDispatch*)* pRetVal);  
```  
  
 Należy pamiętać, że ignoruje Tlbexp.exe <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> pola.  
  
 Ponieważ biblioteki typów nie mogą pomieścić wszystkich informacji znajdujących się w zestawach, Tlbexp.exe może odrzucić niektóre dane podczas procesu eksportu. Wyjaśnienie proces transformacji i identyfikator źródła każdego z nich wysyłanego do biblioteki typów informacji, zobacz [zestawu do typu biblioteki konwersja — Podsumowanie](http://msdn.microsoft.com/library/3a37eefb-a76c-4000-9080-7dbbf66a4896).  
  
 Należy pamiętać, że eksporter biblioteki typów eksportuje metod, które mają <xref:System.TypedReference> parametrów jako `VARIANT`, mimo że <xref:System.TypedReference> obiekt nie ma znaczenia, za pomocą kodu niezarządzanego. Podczas eksportowania metod, które mają <xref:System.TypedReference> parametrów, eksporter biblioteki typów nie będą generowane żadne ostrzeżenia lub błędu i kodu niezarządzanego korzystającej wynikowy biblioteki typów nie będzie działać prawidłowo.  
  
 Eksporter biblioteki typów jest obsługiwany w systemie Microsoft Windows 2000 i nowszych.  
  
## <a name="examples"></a>Przykłady  
 Polecenie generuje biblioteki typów o takiej samej nazwie jak odnaleźć zestawu w `myTest.dll`.  
  
```  
tlbexp myTest.dll  
```  
  
 Polecenie generuje biblioteki typów o nazwie `clipper.tlb`.  
  
```  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 Poniższy przykład ilustruje użycie Tlbexp.exe do eksportowania biblioteki typów z zestawu, który odwołuje się do zestawów importowanych przy użyciu Tlbimp.exe.  
  
 Tlbimp.exe należy najpierw użyć do zaimportowania do biblioteki typów `myLib.tlb` i zapisz go jako `myLib.dll`.  
  
```  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 Polecenie używa kompilatora C# do skompilowania `Sample.dll,` odwołującego `myLib.dll` utworzony w poprzednim przykładzie.  
  
```  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 Polecenie generuje biblioteki typów dla `Sample.dll` , która odwołuje się `myLib.dll`.  
  
```  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.TypeLibExporterFlags>  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Regasm.exe (narzędzie rejestracji zestawów)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 [Zestaw do typu biblioteki konwersja — podsumowanie](http://msdn.microsoft.com/library/3a37eefb-a76c-4000-9080-7dbbf66a4896)  
 [Tlbimp.exe (importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
