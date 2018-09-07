---
title: -link (Visual Basic)
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
ms.openlocfilehash: 833c0c017d0a9b758dc18273c1fc48fddc1c261d
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083253"
---
# <a name="-link-visual-basic"></a>-link (Visual Basic)
Powoduje, że kompilator udostępnia informacje o typie modelu COM w określonych zestawach do projektu, który obecnie kompilacja.  
  
## <a name="syntax"></a>Składnia  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`fileList`|Wymagane. Rozdzielana przecinkami lista nazw plików zestawu. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu.|  
  
## <a name="remarks"></a>Uwagi  
 `-link` Opcja służy do wdrażania aplikacji, która zawiera osadzone informacje o typie. Aplikacja następnie można użyć typów w zestawie środowiska uruchomieniowego, które implementują informacje o typie osadzony bez odwołania do zestawu środowiska wykonawczego. Jeśli różne wersje zestawów środowiska uruchomieniowego są publikowane, aplikacji, która zawiera informacje o typie osadzony pracować z różnymi wersjami bez konieczności zostać zrekompilowane. Aby uzyskać przykład, zobacz [wskazówki: osadzanie typów z zarządzanych zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md).  
  
 Za pomocą `-link` opcja jest szczególnie przydatna w przypadku, gdy pracujesz za pomocą modelu COM. Można osadzić typów modelu COM, dzięki czemu aplikacja nie wymaga już podstawowego zestawu międzyoperacyjnego (PIA) na komputerze docelowym. `-link` Opcja nakazuje kompilatorowi osadzanie informacji o typie modelu COM z odwołania zestawu międzyoperacyjnego wynikowy kod skompilowany. Typ COM jest identyfikowany przez wartość identyfikatora CLSID (GUID). W rezultacie aplikację można uruchomić na komputerze docelowym, w której zainstalowano te same typy modelu COM za pomocą tych samych wartości identyfikatora CLSID. Aplikacje, które automatyzują Microsoft Office są dobrym przykładem. Ponieważ aplikacji, takich jak Office zwykle zachować tę samą wartość identyfikatora CLSID różnych wersji, aplikacja może używać typów modelu COM, jak długo, jak .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym, a Twoja aplikacja używa metod, właściwości lub zdarzenia, które są zawarte w przywoływanych typów modelu COM.  
  
 `-link` Opcja osadza interfejsy, struktury i delegatów. Osadzanie klasy COM nie jest obsługiwane.  
  
> [!NOTE]
>  Podczas tworzenia wystąpienia typu osadzonego modelu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu. Próba utworzenia wystąpienia typu osadzonego modelu COM za pomocą wspólna spowoduje wystąpienie błędu.  
  
 Aby ustawić `-link` opcji w programie Visual Studio, Dodaj odwołanie do zestawu i ustaw `Embed Interop Types` właściwości **true**. Wartość domyślna dla `Embed Interop Types` właściwość **false**.  
  
 Jeśli łączysz się do zestawu COM (Assembly A) która sama odwołuje się do innego zestawu modelu COM (Assembly B), musisz również link do zestawu B, jeśli jest spełniony jeden z następujących czynności:  
  
-   Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.  
  
-   Pola, właściwości, zdarzenia lub metody, która ma typ lub parametr typu zwracanego z zestawu B zostanie wywołana.  
  
 Użyj [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) określić katalog, w którym znajduje się co najmniej jeden z odwołania do zestawów.  
  
 Podobnie jak [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) — opcja kompilatora, `-link` — opcja kompilatora korzysta z pliku odpowiedzi Vbc.rsp odwołania często używane [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów. Użyj [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) opcji kompilatora, jeśli nie chcesz, aby kompilator korzystać soubor Vbc.rsp.  
  
 Krótkiej formy `-link` jest `-l`.  
  
## <a name="generics-and-embedded-types"></a>Typy ogólne i osadzone typy  
 W poniższych sekcjach opisano ograniczenia dotyczące używania typów ogólnych w aplikacjach, które osadzić typów międzyoperacyjnych.  
  
### <a name="generic-interfaces"></a>Interfejsy ogólne  
 Nie można używać interfejsów ogólnych, które są osadzone w zestaw międzyoperacyjny. Jest to pokazane w poniższym przykładzie.  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, które mają parametry ogólne  
 Typy, które mają parametr ogólny, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć Jeśli typ jest z zestawu zewnętrznego. To ograniczenie nie ma zastosowania do interfejsów. Na przykład, rozważmy <xref:Microsoft.Office.Interop.Excel.Range> interfejsu, który jest zdefiniowany w <xref:Microsoft.Office.Interop.Excel> zestawu. Jeśli biblioteka osadza typów międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i udostępnia metodę, która zwraca typ ogólny, który ma parametr, którego typ jest <xref:Microsoft.Office.Interop.Excel.Range> interfejsu i metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 W poniższym przykładzie, kod klienta może wywołać metodę, która zwraca <xref:System.Collections.IList> interfejs ogólny bez błędów.  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje plik źródłowy `OfficeApp.vb` i odwoływać się do zestawów z `COMData1.dll` i `COMData2.dll` do produkcji `OfficeApp.exe`.  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
- [Przewodnik: osadzanie typów z zarządzanych zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
- [— Odwołanie (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
- [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)  
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
- [Wprowadzenie do usługi międzyoperacyjnej modelu COM](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
