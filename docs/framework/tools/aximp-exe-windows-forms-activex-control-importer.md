---
title: Aximp.exe (Importer kontrolki ActiveX formularzy systemu Windows)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ActiveX controls, hosting in Windows Forms
- ActiveX Control Importer
- type definitions, converting
- Aximp.exe
- Windows Forms ActiveX Control Importer
ms.assetid: 482c0d83-7144-4497-b626-87d2351b78d0
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 61f0fc0a157e80499bbc4da4d99bcd6ed15ddefd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="aximpexe-windows-forms-activex-control-importer"></a>Aximp.exe (Importer kontrolki ActiveX formularzy systemu Windows)
Importer formantów ActiveX konwertuje definicje typów w bibliotece typów modelu COM dla formantu ActiveX na formant programu Windows Forms.  
  
 Formularze systemu Windows może zawierać tylko formanty formularzy systemu Windows — to znaczy klasy, które pochodzą od <xref:System.Windows.Forms.Control>. Program Aximp.exe generuje klasę otoki dla formantu ActiveX, którą można obsługiwać w programie Windows Form. Dzięki temu można korzystać z metodologii obsługi w czasie projektowania i programowania, która jest stosowana do innych formantów programu Windows Forms.  
  
 Do hostowania formantu ActiveX, należy wygenerować otoki kontrolkę, która jest pochodną <xref:System.Windows.Forms.AxHost>. Ten formant otoki zawiera wystąpienie źródłowego formantu ActiveX. Umożliwia on komunikację z formantem ActiveX, ale jest widoczny jako formant programu Windows Forms. Ten wygenerowany formant obsługuje formant ActiveX i uwidacznia jego właściwości, metody i zdarzenia, tak jakby należały do wygenerowanego formantu.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
aximp [options]{file.dll | file.ocx}  
```  
  
## <a name="remarks"></a>Uwagi  
  
|Argument|Opis|  
|--------------|-----------------|  
|*plik*|Nazwa pliku źródłowego, który zawiera formant ActiveX do przekonwertowania. Argument file musi mieć rozszerzenie dll lub ocx.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|`/delaysign`|Określa, że program Aximp.exe ma podpisać wynikowy formant, używając funkcji podpisywania opóźnionego. Tę opcję należy określić przy użyciu jednej `/keycontainer:`, `/keyfile:`, lub `/publickey:` opcji. Aby uzyskać więcej informacji na opóźnione proces podpisywania, zobacz [opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md).|  
|`/help`|Wyświetla składnię polecenia i opcje narzędzia.|  
|`/keycontainer:`*containerName*|Podpisuje utworzony formant przy użyciu silnej nazwy przy użyciu pary kluczy publiczny/prywatny znaleziony w określone przez kontener kluczy *containerName*.|  
|`/keyfile:`*filename*|Podpisuje utworzony formant przy użyciu silnej nazwy za pomocą wydawcy oficjalnego publicznego i prywatnego pary kluczy w *filename*.|  
|`/nologo`|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|`/out:`*filename*|Określa nazwę zestawu, który ma zostać utworzony.|  
|`/publickey:`*filename*|Podpisuje utworzony formant przy użyciu silnej nazwy przy użyciu klucza publicznego można odnaleźć pliku określonego przez *filename*.|  
|`/rcw:`*filename*|Używa określonej wywoływalnej otoki czasu wykonywania, zamiast generować nową. Można określić wiele wystąpień. Dla ścieżek względnych jest używany bieżący katalog. Aby uzyskać więcej informacji, zobacz [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md).|  
|`/silent`|Pomija wyświetlanie komunikatów o sukcesie.|  
|`/source`|Generuje kod źródłowy w języku C# dla otoki programu Windows Forms.|  
|`/verbose`|Określa tryb pełny; wyświetla dodatkowe informacje o postępie.|  
|`/?`|Wyświetla składnię polecenia i opcje narzędzia.|  
  
 Program Aximp.exe konwertuje całą bibliotekę typów formantu ActiveX jednocześnie i tworzy zbiór zestawów zawierający metadane środowiska uruchomieniowego języka wspólnego oraz implementację formantu dla typów zdefiniowanych w oryginalnej bibliotece typów. Nazwy wygenerowanych plików są określane według następującego wzorca:  
  
 Typowe proxy środowiska uruchomieniowego języka dla typów COM: *progid*.dll  
  
 Serwer proxy formularzy systemu Windows dla formantów ActiveX (gdzie Ax oznacza ActiveX): Ax*progid*.dll  
  
> [!NOTE]
>  Jeśli nazwa składowej formantu ActiveX pasuje do nazwy zdefiniowanej w programie .NET Framework, program Aximp.exe poprzedzi nazwę składowej prefiksem „Ctl”, gdy będzie tworzyć klasę pochodną AxHost. Na przykład jeśli formant ActiveX ma składową o nazwie Layout, jej nazwa w klasie pochodnej AxHost zostanie zmieniona na CtlLayout, ponieważ zdarzenie Layout jest zdefiniowane w programie .NET Framework.  
  
 Można sprawdzić tych plików wygenerowanych przy użyciu narzędzi, takich jak [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).  
  
 Nie można używać programu Aximp.exe do generowania zestawu platformy .NET dla formantu ActiveX WebBrowser.  
  
 Po uruchomieniu programu Aximp.exe dla biblioteki shdocvw.dll zawsze jest tworzony inny plik o nazwie shdocvw.dll w katalogu, z którego uruchomiono narzędzie. Jeśli ten wygenerowany plik zostanie umieszczony w katalogu Documents and Settings, będzie powodował problemy w programach Microsoft Internet Explorer i Eksplorator Windows. Gdy komputer jest uruchamiany ponownie, system Windows najpierw szuka kopii pliku shdocvw.dll w katalogu Documents and Settings, a dopiero potem w katalogu system32. Użyje kopii znalezionej w katalogu Documents and Settings i podejmie próbę załadowania zarządzanych otok. Programy Internet Explorer i Eksplorator Windows nie będą działać prawidłowo, ponieważ są zależne od aparatu renderowania znajdującego się w wersji pliku shdocvw.dll przechowywanej w katalogu system32. Jeśli wystąpi ten problem, usuń kopię pliku shdocvw.dll z katalogu Documents and Settings i uruchom ponownie komputer.  
  
 Użycie programu Aximp.exe z biblioteką shdocvw.dll w celu utworzenia formantu platformy .NET, który będzie używany podczas tworzenia aplikacji, także może powodować problemy. W tym przypadku aplikacja będzie ładować obie wersje biblioteki shdocvw.dll (systemową i wygenerowaną) i może nadać priorytet wersji systemowej. Gdy w takiej sytuacji użytkownik podejmie próbę załadowania strony sieci Web w formancie ActiveX WebBrowser, może zostać wyświetlone okno dialogowe Otwieranie/Zapisywanie. Po kliknięciu przez użytkownika **Otwórz**, strony sieci Web zostanie otwarty w programie Internet Explorer. Dzieje się tak tylko na komputerach, na których jest używany program Internet Explorer w wersji 6 lub starszy. Aby zapobiec temu problemowi, należy użyć zarządzanej <xref:System.Windows.Forms.WebBrowser> kontrolować lub użyj [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] do generowania zarządzanego shdocvw.dll zgodnie z opisem w [porady: Dodawanie odwołania do bibliotek typów](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md).  
  
## <a name="example"></a>Przykład  
 Polecenie generuje MediaPlayer.dll i AxMediaPlayer.dll formantu Media Player `msdxm.ocx`.  
  
```  
aximp c:\systemroot\system32\msdxm.ocx  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
