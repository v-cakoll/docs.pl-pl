---
title: -link
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: 6082806591d398aa8b16b44e769a3f8078ce62d9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387741"
---
# <a name="-link-visual-basic"></a>-Link (Visual Basic)
Powoduje, że kompilator udostępnia informacje o typie COM w określonych zestawach, które są dostępne dla aktualnie kompilowanego projektu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-link:fileList  
```

lub  

```console
-l:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`fileList`|Wymagany. Rozdzielana przecinkami lista nazw plików zestawu. Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów.|  
  
## <a name="remarks"></a>Uwagi  
 `-link`Opcja umożliwia wdrożenie aplikacji, która ma informacje o typie osadzonym. Aplikacja może następnie użyć typów w zestawie środowiska uruchomieniowego, który implementuje informacje o typie osadzonym, bez konieczności odwoływania się do zestawu środowiska uruchomieniowego. Jeśli są publikowane różne wersje zestawu środowiska uruchomieniowego, aplikacja zawierająca informacje o typie osadzonym może współdziałać z różnymi wersjami bez konieczności ponownego kompilowania. Aby zapoznać się z przykładem, zobacz [Przewodnik: osadzanie typów z zarządzanych zestawów](../../../standard/assembly/embed-types-visual-studio.md).  
  
 Korzystanie z tej `-link` opcji jest szczególnie przydatne podczas pracy z międzyoperacyjnym modelem com. Można osadzić typy COM, aby aplikacja nie wymagała już podstawowego zestawu międzyoperacyjnego (PIA) na komputerze docelowym. `-link`Opcja instruuje kompilator, aby osadzi informacje o typie com z przywoływanego zestawu międzyoperacyjnego do w wyniku skompilowanego kodu. Typ COM jest identyfikowany przez wartość CLSID (GUID). W związku z tym aplikacja może działać na komputerze docelowym, na którym zainstalowano te same typy COM z tymi samymi wartościami CLSID. Aplikacje automatyzujące Microsoft Office są dobrym przykładem. Ponieważ aplikacje, takie jak pakiet Office, zwykle zachowują tę samą wartość CLSID w różnych wersjach, aplikacja może używać typów COM, których dotyczy odwołanie, tak długo, jak .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym, a aplikacja korzysta z metod, właściwości lub zdarzeń, które znajdują się w przywoływanych typach COM.  
  
 `-link`Opcja osadza tylko interfejsy, struktury i delegatów. Osadzanie klas COM nie jest obsługiwane.  
  
> [!NOTE]
> Podczas tworzenia wystąpienia osadzonego typu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu. Próba utworzenia wystąpienia osadzonego typu COM przy użyciu klasy coclass powoduje wystąpienie błędu.  
  
 Aby ustawić `-link` opcję w programie Visual Studio, Dodaj odwołanie do zestawu i ustaw `Embed Interop Types` Właściwość na **wartość true**. Wartość domyślna dla `Embed Interop Types` właściwości ma **wartość false**.  
  
 Jeśli utworzysz link do zestawu COM (zestawu A), który sam odwołuje się do innego zestawu COM (zestawu B), musisz także połączyć się z zestawem B, jeśli jest spełniony jeden z następujących warunków:  
  
- Typ z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.  
  
- Wywołano pole, właściwość, zdarzenie lub metodę z typem zwracanym lub typem parametru z zestawu B.  
  
 Użyj [-LIBPATH](libpath.md) , aby określić katalog, w którym znajduje się co najmniej jedno odwołanie do zestawu.  
  
 Podobnie jak w przypadku opcji kompilatora [odwołania](reference.md) , `-link` Opcja kompilatora używa pliku odpowiedzi VBC. rsp, który odwołuje się do często używanych zestawów .NET Framework. Użyj opcji kompilatora [-noconfig](noconfig.md) , jeśli nie chcesz, aby kompilator używał pliku VBC. rsp.  
  
 Krótka forma `-link` to `-l` .  
  
## <a name="generics-and-embedded-types"></a>Typy ogólne i osadzone  
 W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzają typy międzyoperacyjnych.  
  
### <a name="generic-interfaces"></a>Interfejsy ogólne  
 Nie można użyć ogólnych interfejsów, które są osadzone z zestawu międzyoperacyjnego. Pokazano to w poniższym przykładzie.  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, które mają parametry ogólne  
 Typów, które mają parametr generyczny, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć, jeśli ten typ pochodzi z zewnętrznego zestawu. To ograniczenie nie ma zastosowania do interfejsów. Rozważmy na przykład <xref:Microsoft.Office.Interop.Excel.Range> interfejs, który jest zdefiniowany w <xref:Microsoft.Office.Interop.Excel> zestawie. Jeśli biblioteka osadza typy międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i uwidacznia metodę, która zwraca typ ogólny, który ma parametr, którego typem jest <xref:Microsoft.Office.Interop.Excel.Range> interfejs, ta metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 W poniższym przykładzie kod klienta może wywołać metodę, która zwraca <xref:System.Collections.IList> interfejs generyczny bez błędu.  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a>Przykład  
 Poniższy wiersz polecenia kompiluje pliki źródłowe `OfficeApp.vb` i zestawy odwołań z `COMData1.dll` i `COMData2.dll` do produkcji `OfficeApp.exe` .  
  
```console  
vbc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Przewodnik: osadzanie typów z zarządzanych zestawów](../../../standard/assembly/embed-types-visual-studio.md)
- [-Reference (Visual Basic)](reference.md)
- [-noconfig](noconfig.md)
- [-libpath](libpath.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
- [Wprowadzenie do usługi międzyoperacyjnej modelu COM](../../programming-guide/com-interop/introduction-to-com-interop.md)
