---
title: Aximp.exe (Importer kontrolki ActiveX formularzy systemu Windows)
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls, hosting in Windows Forms
- ActiveX Control Importer
- type definitions, converting
- Aximp.exe
- Windows Forms ActiveX Control Importer
ms.assetid: 482c0d83-7144-4497-b626-87d2351b78d0
ms.openlocfilehash: a1b061b480b3e22b136a6373ddb87cf9d2233457
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715784"
---
# <a name="aximpexe-windows-forms-activex-control-importer"></a>Aximp.exe (Importer kontrolki ActiveX formularzy systemu Windows)
Importer formantów ActiveX konwertuje definicje typów w bibliotece typów modelu COM dla formantu ActiveX na formant programu Windows Forms.  
  
 Windows Forms można hostować tylko kontrolki Windows Forms, czyli klasy, które pochodzą z <xref:System.Windows.Forms.Control>. Program Aximp.exe generuje klasę otoki dla formantu ActiveX, którą można obsługiwać w programie Windows Form. Dzięki temu można korzystać z metodologii obsługi w czasie projektowania i programowania, która jest stosowana do innych formantów programu Windows Forms.  
  
 Aby hostować formant ActiveX, należy wygenerować formant otoki pochodzący z <xref:System.Windows.Forms.AxHost>. Ten formant otoki zawiera wystąpienie źródłowego formantu ActiveX. Umożliwia on komunikację z formantem ActiveX, ale jest widoczny jako formant programu Windows Forms. Ten wygenerowany formant obsługuje formant ActiveX i uwidacznia jego właściwości, metody i zdarzenia, tak jakby należały do wygenerowanego formantu.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
aximp [options]{file.dll | file.ocx}  
```  
  
## <a name="remarks"></a>Uwagi  
  
|Argument|Opis|  
|--------------|-----------------|  
|*rozszerzeniem*|Nazwa pliku źródłowego, który zawiera formant ActiveX do przekonwertowania. Argument file musi mieć rozszerzenie dll lub ocx.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/delaysign`|Określa, że program Aximp.exe ma podpisać wynikowy formant, używając funkcji podpisywania opóźnionego. Należy określić tę opcję z opcją `/keycontainer:`, `/keyfile:`lub `/publickey:`. Aby uzyskać więcej informacji o opóźnionym procesie podpisywania, zobacz [opóźnienie podpisywania zestawu](../../standard/assembly/delay-sign.md).|  
|`/help`|Wyświetla składnię polecenia i opcje narzędzia.|  
|`/keycontainer:` *ContainerName*|Podpisuje formant o silnej nazwie przy użyciu pary kluczy publicznych/prywatnych znalezionych w kontenerze kluczy określonym przez *ContainerName*.|  
|*Nazwa pliku* `/keyfile:`|Podpisuje kontrolkę będącą silną nazwą, używając oficjalnej pary kluczy publiczny/prywatny wydawcy, która została znaleziona w *pliku filename*.|  
|`/nologo`|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|*Nazwa pliku* `/out:`|Określa nazwę zestawu, który ma zostać utworzony.|  
|*Nazwa pliku* `/publickey:`|Podpisuje formant o silnej nazwie przy użyciu klucza publicznego znajdującego się w pliku określonym przez *nazwę pliku*.|  
|*Nazwa pliku* `/rcw:`|Używa określonej wywoływalnej otoki czasu wykonywania, zamiast generować nową. Można określić wiele wystąpień. Dla ścieżek względnych jest używany bieżący katalog. Aby uzyskać więcej informacji, zobacz [otoka wywoływana w środowisku uruchomieniowym](../../standard/native-interop/runtime-callable-wrapper.md).|  
|`/silent`|Pomija wyświetlanie komunikatów o sukcesie.|  
|`/source`|Generuje kod źródłowy w języku C# dla otoki programu Windows Forms.|  
|`/verbose`|Określa tryb pełny; wyświetla dodatkowe informacje o postępie.|  
|`/?`|Wyświetla składnię polecenia i opcje narzędzia.|  
  
 Program Aximp.exe konwertuje całą bibliotekę typów formantu ActiveX jednocześnie i tworzy zbiór zestawów zawierający metadane środowiska uruchomieniowego języka wspólnego oraz implementację formantu dla typów zdefiniowanych w oryginalnej bibliotece typów. Nazwy wygenerowanych plików są określane według następującego wzorca:  
  
 serwer proxy środowiska uruchomieniowego języka wspólnego dla typów COM: *ProgID*. dll  
  
 Windows Forms proxy dla formantów ActiveX (gdzie AX oznacza ActiveX): AX*ProgID*. dll  
  
> [!NOTE]
> Jeśli nazwa składowej formantu ActiveX pasuje do nazwy zdefiniowanej w programie .NET Framework, program Aximp.exe poprzedzi nazwę składowej prefiksem „Ctl”, gdy będzie tworzyć klasę pochodną AxHost. Na przykład jeśli formant ActiveX ma składową o nazwie Layout, jej nazwa w klasie pochodnej AxHost zostanie zmieniona na CtlLayout, ponieważ zdarzenie Layout jest zdefiniowane w programie .NET Framework.  
  
 Te wygenerowane pliki można przeanalizować za pomocą narzędzi, takich jak [Ildasm. exe (Il dezasembler)](ildasm-exe-il-disassembler.md).  
  
 Nie można używać programu Aximp.exe do generowania zestawu platformy .NET dla formantu ActiveX WebBrowser.  
  
 Po uruchomieniu programu Aximp.exe dla biblioteki shdocvw.dll zawsze jest tworzony inny plik o nazwie shdocvw.dll w katalogu, z którego uruchomiono narzędzie. Jeśli ten wygenerowany plik zostanie umieszczony w katalogu Documents and Settings, będzie powodował problemy w programach Microsoft Internet Explorer i Eksplorator Windows. Gdy komputer jest uruchamiany ponownie, system Windows najpierw szuka kopii pliku shdocvw.dll w katalogu Documents and Settings, a dopiero potem w katalogu system32. Użyje kopii znalezionej w katalogu Documents and Settings i podejmie próbę załadowania zarządzanych otok. Programy Internet Explorer i Eksplorator Windows nie będą działać prawidłowo, ponieważ są zależne od aparatu renderowania znajdującego się w wersji pliku shdocvw.dll przechowywanej w katalogu system32. Jeśli wystąpi ten problem, usuń kopię pliku shdocvw.dll z katalogu Documents and Settings i uruchom ponownie komputer.  
  
 Użycie programu Aximp.exe z biblioteką shdocvw.dll w celu utworzenia formantu platformy .NET, który będzie używany podczas tworzenia aplikacji, także może powodować problemy. W tym przypadku aplikacja będzie ładować obie wersje biblioteki shdocvw.dll (systemową i wygenerowaną) i może nadać priorytet wersji systemowej. Gdy w takiej sytuacji użytkownik podejmie próbę załadowania strony sieci Web w formancie ActiveX WebBrowser, może zostać wyświetlone okno dialogowe Otwieranie/Zapisywanie. Gdy użytkownik kliknie przycisk **Otwórz**, zostanie otwarta strona sieci Web w programie Internet Explorer. Dzieje się tak tylko na komputerach, na których jest używany program Internet Explorer w wersji 6 lub starszy. Aby zapobiec temu problemowi, użyj zarządzanego formantu <xref:System.Windows.Forms.WebBrowser> lub użyj programu Visual Studio do wygenerowania zarządzanej biblioteki Shdocvw. dll zgodnie z opisem w artykule [jak: Dodawanie odwołań do bibliotek typów](../interop/how-to-add-references-to-type-libraries.md).  
  
## <a name="example"></a>Przykład  
 Następujące polecenie generuje MediaPlayer. dll i AxMediaPlayer. dll dla `msdxm.ocx`formantu Media Player.  
  
```console 
aximp c:\systemroot\system32\msdxm.ocx  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Ildasm.exe (dezasembler IL)](ildasm-exe-il-disassembler.md)
