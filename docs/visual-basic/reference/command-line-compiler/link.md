---
title: -link (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4410818b43c0ab12f9488198fffbe4b0f2d89252
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-link-visual-basic"></a>-link (Visual Basic)
Powoduje, że kompilator, aby udostępnić informacje o typie modelu COM w określonych zestawów do projektu, które są aktualnie kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
-link:fileList  
' -or-  
-l:fileList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`fileList`|Wymagany. Rozdzielana przecinkami lista nazw plików zestawu. Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów.|  
  
## <a name="remarks"></a>Uwagi  
 `-link` Opcja umożliwia wdrażanie aplikacji, która zawiera osadzone informacji o typie. Aplikacja może następnie używać typów w zestawie środowiska uruchomieniowego, które implementują informacji osadzonym typem bez konieczności odwołanie do zestawu środowiska wykonawczego. Jeśli w różnych wersjach zestawu środowiska wykonawczego są publikowane, aplikacji, który zawiera informacje o osadzonym typem może współpracować z różnych wersji bez konieczności ponownie skompilowana. Na przykład zobacz [wskazówki: osadzanie typów z zarządzanych zestawów](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).  
  
 Przy użyciu `-link` opcja jest szczególnie przydatne podczas pracy z COM interop. Można osadzić typów COM, aby aplikacja nie wymaga już podstawowy zestaw międzyoperacyjny (PIA) na komputerze docelowym. `-link` Opcja nakazuje kompilatorowi osadzanie informacji o typie COM z przywoływanego zestawu międzyoperacyjnego na wynikowej skompilowanego kodu. Typ modelu COM jest identyfikowany przez wartość identyfikatora CLSID (GUID). W związku z tym aplikację można uruchomić na komputerze docelowym, który zainstalował takich samych typach modelu COM przy użyciu tej samej wartości identyfikatora CLSID. Dobrym przykładem są aplikacje, które automatyzują Microsoft Office. Ponieważ aplikacji, takich jak Office zazwyczaj zachować taką samą wartość identyfikatora CLSID w różnych wersjach, aplikacja może używać wskazanych typów COM, jak długo jako .NET Framework 4 lub nowszy jest zainstalowany na komputerze docelowym i aplikacja korzysta z metod, właściwości lub zdarzenia, które są objęte wskazanych typów COM.  
  
 `-link` Opcja osadza interfejsów, struktur i delegatów. Osadzanie klasy COM nie jest obsługiwane.  
  
> [!NOTE]
>  Podczas tworzenia wystąpienia typu osadzonego modelu COM w kodzie, należy utworzyć wystąpienie przy użyciu odpowiedniego interfejsu. Podjęto próbę utworzenia wystąpienia typu osadzonego modelu COM za pomocą klasy CoClass powoduje błąd.  
  
 Aby ustawić `-link` opcji w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], Dodaj odwołanie do zestawu danych i ustaw `Embed Interop Types` właściwości **true**. Wartość domyślna dla `Embed Interop Types` właściwość jest **false**.  
  
 Gdy łącze do zestawu COM (zestaw A) które odwołuje się do innego zestawu COM (zestaw B), należy także łącze do zestawu B, jeśli spełniony jest jeden z następujących czynności:  
  
-   Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.  
  
-   Pola, właściwości, zdarzenia lub metodę, która ma zwracany typ lub parametr typu z B zestawu jest wywoływany.  
  
 Użyj [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) Aby określić katalog, w którym znajduje się co najmniej jednego odwołania do zestawów.  
  
 Podobnie jak [/reference](../../../visual-basic/reference/command-line-compiler/reference.md) — opcja kompilatora, `-link` — opcja kompilatora używa Vbc.rsp plik odpowiedzi, który odwołuje się do często używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów. Użyj [- noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) opcję kompilatora, jeśli nie chcesz kompilatora, aby użyć pliku Vbc.rsp.  
  
 Krótka forma z `-link` jest `-l`.  
  
## <a name="generics-and-embedded-types"></a>Typy ogólne i osadzone typy  
 W poniższych sekcjach opisano ograniczenia przy użyciu typów ogólnych w aplikacjach, które osadzić typów międzyoperacyjnych.  
  
### <a name="generic-interfaces"></a>Interfejsy ogólne  
 Nie można używać interfejsów ogólnych osadzonych z zestawu międzyoperacyjnego. Przedstawiono to w poniższym przykładzie.  
  
 [!code-vb[VbLinkCompiler#1](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_1.vb)]  
  
### <a name="types-that-have-generic-parameters"></a>Typy, które mają parametry ogólne  
 Typy, które mają parametru ogólnego, którego typ jest osadzony z zestawu międzyoperacyjnego nie można użyć Jeśli typ jest z zewnętrznego zestawu. To ograniczenie nie ma zastosowania do interfejsów. Rozważmy na przykład <xref:Microsoft.Office.Interop.Excel.Range> interfejs, który jest zdefiniowany w <xref:Microsoft.Office.Interop.Excel> zestawu. Jeśli biblioteki osadza typów międzyoperacyjnych z <xref:Microsoft.Office.Interop.Excel> zestawu i udostępnia metodę, która zwraca wartość typu ogólnego, który ma parametr typu jest <xref:Microsoft.Office.Interop.Excel.Range> interfejsu, metoda musi zwracać interfejs ogólny, jak pokazano w poniższym przykładzie kodu.  
  
 [!code-vb[VbLinkCompiler#2](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_2.vb)]  
[!code-vb[VbLinkCompiler#3](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_3.vb)]  
[!code-vb[VbLinkCompiler#4](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_4.vb)]  
  
 W poniższym przykładzie kodu klienta można wywołać metodę, która zwraca <xref:System.Collections.IList> ogólny interfejs bez błędów.  
  
 [!code-vb[VbLinkCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/link_5.vb)]  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie kompiluje plik źródłowy `OfficeApp.vb` i odwołuje się do zestawów z `COMData1.dll` i `COMData2.dll` do produkcji `OfficeApp.exe`.  
  
```console  
vbc -link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przewodnik: osadzanie typów z zarządzanych zestawów](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [-odwołania (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Wprowadzenie do usługi międzyoperacyjnej modelu COM](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)
