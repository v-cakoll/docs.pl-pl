---
title: Odwołania do elementów zadeklarowanych
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: a6477a9f0abaf8eb9176f4f6ab2a920af6c8f500
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345303"
---
# <a name="references-to-declared-elements-visual-basic"></a>Odwołania do elementów zadeklarowanych (Visual Basic)
Gdy kod odwołuje się do zadeklarowanego elementu, kompilator Visual Basic dopasowuje nazwę w odwołaniu do odpowiedniej deklaracji tej nazwy. Jeśli jest zadeklarowany więcej niż jeden element o tej samej nazwie, można kontrolować, które z tych elementów mają być przywoływane przez *zakwalifikowanie* jego nazwy.  
  
 Kompilator próbuje dopasować odwołanie do nazwy do deklaracji nazwy z *najwęższym zakresem*. Oznacza to, że zaczyna się od kodu, który wprowadza odwołanie i działa na zewnątrz przez kolejne poziomy zawierające elementy.  
  
 Poniższy przykład przedstawia odwołania do dwóch zmiennych o tej samej nazwie. Przykład deklaruje dwie zmienne, z których każda o nazwie `totalCount`, na różnych poziomach zakresu w `container`modułu. Gdy procedura `showCount` wyświetla `totalCount` bez kwalifikacji, kompilator Visual Basic rozpoznaje odwołanie do deklaracji z najwęższym zakresem, a mianowicie lokalną deklarację w `showCount`. Gdy kwalifikuje `totalCount` z `container`modułu, kompilator rozpoznaje odwołanie do deklaracji z szerszym zakresem.  
  
```vb  
' Assume these two modules are both in the same assembly.  
Module container  
    Public totalCount As Integer = 1  
    Public Sub showCount()  
        Dim totalCount As Integer = 6000  
        ' The following statement displays the local totalCount (6000).  
        MsgBox("Unqualified totalCount is " & CStr(totalCount))  
        ' The following statement displays the module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
Module callingModule  
    Public Sub displayCount()  
        container.showCount()  
        ' The following statement displays the containing module's totalCount (1).  
        MsgBox("container.totalCount is " & CStr(container.totalCount))  
    End Sub  
End Module  
```  
  
## <a name="qualifying-an-element-name"></a>Kwalifikowanie nazwy elementu  
 Jeśli chcesz przesłonić ten proces wyszukiwania i określić nazwę zadeklarowaną w szerszym zakresie, musisz *zakwalifikować* nazwę z elementem zawierającym szerszy zakres. W niektórych przypadkach może być również konieczne zakwalifikowanie elementu zawierającego.  
  
 Kwalifikowanie nazwy oznacza poprzedzające ją w instrukcji źródłowej informacjami, które identyfikują, gdzie jest zdefiniowany element docelowy. Te informacje są nazywane *ciągiem kwalifikacji*. Może zawierać co najmniej jedną przestrzeń nazw oraz moduł, klasę lub strukturę.  
  
 Ciąg kwalifikacji powinien jednoznacznie określać moduł, klasę lub strukturę zawierające element docelowy. Kontener może być umieszczony w innym elemencie zawierającym, zazwyczaj przestrzeni nazw. Może być konieczne dołączenie do ciągu kwalifikacji kilku elementów zawierających elementy.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Aby uzyskać dostęp do zadeklarowanego elementu przez zakwalifikowanie jego nazwy  
  
1. Określ lokalizację, w której element został zdefiniowany. Może to obejmować przestrzeń nazw, a nawet hierarchię przestrzeni nazw. W przestrzeni nazw najniższego poziomu element musi być zawarty w module, klasie lub strukturze.  
  
    ```vb  
    ' Assume the following hierarchy exists outside your code.  
    Namespace outerSpace  
        Namespace innerSpace  
            Module holdsTotals  
                Public Structure totals  
                    Public thisTotal As Integer  
                    Public Shared grandTotal As Long  
                End Structure  
            End Module  
        End Namespace  
    End Namespace  
    ```  
  
2. Określ ścieżkę kwalifikacyjną na podstawie lokalizacji elementu docelowego. Zacznij od przestrzeni nazw najwyższego poziomu, Kontynuuj do przestrzeni nazw najniższego poziomu i kończyć się modułem, klasą lub strukturą zawierającą element docelowy. Każdy element w ścieżce musi zawierać element, który następuje po nim.  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3. Przygotuj ciąg kwalifikacji dla elementu docelowego. Umieść kropkę (`.`) po każdym elemencie w ścieżce. Aplikacja musi mieć dostęp do każdego elementu w ciągu kwalifikacji.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4. Napisz wyrażenie lub instrukcję przypisania odwołującą się do elementu docelowego w normalny sposób.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5. Poprzedź nazwę elementu docelowego ciągiem kwalifikacji. Nazwa powinna natychmiast podążać za kropką (`.`), która następuje po module, klasie lub strukturze zawierającej element.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6. Kompilator używa ciągu kwalifikacji do znalezienia jasnej, jednoznacznej deklaracji, do której może być zgodny z odwołaniem do elementu docelowego.  
  
 Może być również konieczne zakwalifikowanie odwołania do nazwy, jeśli aplikacja ma dostęp do więcej niż jednego elementu programistycznego, który ma taką samą nazwę. Na przykład przestrzenie nazw <xref:System.Windows.Forms> i <xref:System.Web.UI.WebControls> zawierają klasy `Label` (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> i <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>). Jeśli aplikacja używa obu, lub jeśli definiuje własną klasę `Label`, należy rozróżnić różne obiekty `Label`. Uwzględnij przestrzeń nazw lub zaimportuj alias w deklaracji zmiennej. Poniższy przykład używa aliasu importu.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Elementy członkowskie innych zawierających elementy  
 W przypadku korzystania z nieudostępnionej składowej innej klasy lub struktury, należy najpierw zakwalifikować nazwę składowej ze zmienną lub wyrażeniem, które wskazuje na wystąpienie klasy lub struktury. W poniższym przykładzie `demoClass` jest wystąpieniem klasy o nazwie `class1`.  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 Nie można użyć samej nazwy klasy do kwalifikowania elementu członkowskiego, który nie jest [udostępniany](../../../../visual-basic/language-reference/modifiers/shared.md). Najpierw należy utworzyć wystąpienie w zmiennej obiektu (w tym przypadku `demoClass`), a następnie odwołać się do niego przy użyciu nazwy zmiennej.  
  
 Jeśli klasa lub struktura ma `Shared` składową, można kwalifikować tę składową przy użyciu nazwy klasy lub struktury lub ze zmienną lub wyrażeniem, które wskazuje na wystąpienie.  
  
 Moduł nie ma żadnych oddzielnych wystąpień, a wszystkie jego elementy członkowskie są domyślnie `Shared`. W związku z tym należy zakwalifikować element członkowski modułu przy użyciu nazwy modułu.  
  
 Poniższy przykład przedstawia kwalifikowane odwołania do procedur składowych modułu. Przykład deklaruje dwie `Sub` procedury, zarówno nazwane `perform`, w różnych modułach w projekcie. Każdą z nich można określić bez kwalifikacji w ramach własnego modułu, ale musi być kwalifikowana, jeśli istnieje odwołanie z dowolnego miejsca. Ponieważ ostateczne odwołanie w `module3` nie kwalifikuje się `perform`, kompilator nie może rozpoznać tego odwołania.  
  
```vb  
' Assume these three modules are all in the same assembly.  
Module module1  
    Public Sub perform()  
        MsgBox("module1.perform() now returning")  
    End Sub  
End Module  
Module module2  
    Public Sub perform()  
        MsgBox("module2.perform() now returning")  
    End Sub  
    Public Sub doSomething()  
        ' The following statement calls perform in module2, the active module.  
        perform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
    End Sub  
End Module  
Module module3  
    Public Sub callPerform()  
        ' The following statement calls perform in module1.  
        module1.perform()  
        ' The following statement makes an unresolvable name reference  
        ' and therefore generates a COMPILER ERROR.  
        perform() ' INVALID statement  
    End Sub  
End Module  
```  
  
## <a name="references-to-projects"></a>Odwołania do projektów  
 Aby użyć elementów [publicznych](../../../../visual-basic/language-reference/modifiers/public.md) zdefiniowanych w innym projekcie, należy najpierw ustawić *odwołanie* do zestawu lub biblioteki typów tego projektu. Aby ustawić odwołanie, kliknij opcję **Dodaj odwołanie** w menu **projekt** lub użyj opcji kompilatora wiersza polecenia [-Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) .  
  
 Na przykład można użyć modelu obiektów XML .NET Framework. Jeśli ustawisz odwołanie do przestrzeni nazw <xref:System.Xml>, możesz zadeklarować i użyć dowolnej z jej klas, takich jak <xref:System.Xml.XmlDocument>. Poniższy przykład używa <xref:System.Xml.XmlDocument>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Importowanie zawierających elementy  
 Aby *zaimportować* przestrzenie nazw zawierające moduły lub klasy, które mają być używane, można użyć [instrukcji Imports (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) . Dzięki temu można odwołać się do elementów zdefiniowanych w importowanym obszarze nazw bez w pełni kwalifikujących się nazw. Poniższy przykład zapisuje ponownie poprzedni przykład, aby zaimportować przestrzeń nazw <xref:System.Xml>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 Ponadto instrukcja `Imports` może definiować *alias importu* dla każdej zaimportowanej przestrzeni nazw. Może to spowodować, że kod źródłowy jest krótszy i łatwiejszy do odczytania. Poniższy przykład zapisuje ponownie poprzedni przykład, aby użyć `xD` jako aliasu dla <xref:System.Xml> przestrzeni nazw.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 Instrukcja `Imports` nie sprawia, że elementy z innych projektów są dostępne dla Twojej aplikacji. Oznacza to, że nie ma miejsca na ustawienie odwołania. Importowanie przestrzeni nazw powoduje jedynie usunięcie wymagania, aby kwalifikować się do nazw zdefiniowanych w tej przestrzeni nazw.  
  
 Można również użyć instrukcji `Imports`, aby zaimportować moduły, klasy, struktury i wyliczenia. Następnie można użyć elementów członkowskich takich zaimportowanych elementów bez kwalifikacji. Należy jednak zawsze kwalifikować nieudostępniane elementy członkowskie klas i struktur z zmienną lub wyrażeniem, które oblicza wystąpienie klasy lub struktury.  
  
## <a name="naming-guidelines"></a>Wskazówki dotyczące nazewnictwa  
 Po zdefiniowaniu co najmniej dwóch elementów programistycznych, które mają taką samą nazwę, *niejednoznaczność* może wynikać z tego, kiedy kompilator próbuje rozpoznać odwołanie do tej nazwy. Jeśli więcej niż jedna definicja znajduje się w zakresie lub jeśli żadna definicja nie należy do zakresu, odwołanie jest nierozwiązywalny. Aby zapoznać się z przykładem, zobacz sekcję dotyczącą przykładowego odwołania na tej stronie pomocy.  
  
 Można uniknąć niejednoznaczności nazwy, dając wszystkie elementy unikatowymi nazwami. Następnie można utworzyć odwołanie do dowolnego elementu bez konieczności kwalifikowania jego nazwy z przestrzenią nazw, modułem lub klasą. Zmniejszamy również szanse przypadkowego odwołującego się do niewłaściwego elementu.  
  
## <a name="shadowing"></a>Zasłanianie  
 Gdy dwa elementy programistyczne współdzielą tę samą nazwę, jeden z nich może ukryć lub *Zacień*, drugi. Element z cieniem nie jest dostępny dla celów referencyjnych. Zamiast tego, gdy kod używa zasłoniętej nazwy elementu, kompilator Visual Basic rozpoznaje ją jako element przesłaniania. Aby uzyskać bardziej szczegółowe wyjaśnienie z przykładami, zobacz [przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="see-also"></a>Zobacz także

- [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
- [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Operator New](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
