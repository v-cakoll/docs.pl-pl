---
title: Odwołania do elementów zadeklarowanych (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 18f9920891e35517efe7adcfd4c03e03ac771478
ms.sourcegitcommit: 875ecc3ab2437e299b1d50076bd9b878fa8c64de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43238540"
---
# <a name="references-to-declared-elements-visual-basic"></a>Odwołania do elementów zadeklarowanych (Visual Basic)
Gdy kod odwołuje się do element zadeklarowany, kompilator Visual Basic pasuje do nazwy, w której można się odwołać do odpowiedniego zgłoszenia o takiej nazwie. Jeśli więcej niż jeden element jest zadeklarowana za pomocą tej samej nazwie, możesz kontrolować, które z tych elementów ma być przywoływane przez *kwalifikacji* jego nazwę.  
  
 Kompilator podejmuje próbę dopasowania nazwy odwołania do deklaracji nazwy z *najwęższego zakresu*. Oznacza to, rozpoczyna się od kodu, dzięki czemu odwołania i postępuje na zewnątrz do kolejnych poziomów zawierający elementy.  
  
 Poniższy przykład pokazuje odwołania do dwóch zmiennych o takiej samej nazwie. Przykład deklaruje dwie zmienne, każdy o nazwie `totalCount`, na różnych poziomach zakresu w module `container`. Podczas procedury `showCount` Wyświetla `totalCount` bez kwalifikacji, kompilator Visual Basic jest rozpoznawana jako odwołanie do deklaracji z najwęższego zakresu, to znaczy lokalna deklaracja wewnątrz `showCount`. Gdy kwalifikuje się `totalCount` za pomocą modułu zawierającego `container`, kompilator rozwiązuje odwołanie do deklaracji w szerszym zakresie.  
  
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
  
## <a name="qualifying-an-element-name"></a>Kwalifikujące się nazwę elementu  
 Jeśli chcesz zastąpić ten proces wyszukiwania i określić, nazwa zadeklarowana w szerszym zakresie, należy najpierw *kwalifikowania* nazwą zawierającego element szerszy zakres. W niektórych przypadkach może również być kwalifikuj element zawierający.  
  
 Kwalifikowanie oznacza nazwę poprzedzających je w instrukcji źródła informacje określające, w którym definiowany jest element docelowy. Informacja ta jest wywoływana *ciąg kwalifikacji*. Może zawierać jeden lub więcej przestrzeni nazw i modułu, klasy lub struktury.  
  
 Ciąg kwalifikacji jednoznacznie określić modułu, klasy lub struktury zawierającej element docelowy. Kontener z kolei może znajdować się w innym elemencie zawierającego zazwyczaj przestrzeń nazw. Może być konieczne obejmują kilka zawierający elementy w ciągu kwalifikacji.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Dostęp kwalifikowania nazwy zadeklarowanych elementów  
  
1.  Określ lokalizację, w którym zdefiniowano element. Może to obejmować przestrzeni nazw lub nawet hierarchię przestrzeni nazw. W obszarze nazw najniższy poziom elementu muszą być zawarte w module, klasy lub struktury.  
  
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
  
2.  Określ ścieżkę kwalifikacji, na podstawie lokalizacji elementu docelowego. Uruchom z przestrzenią nazw najwyższego poziomu, przejdź do obszaru nazw najniższy poziom, a kończyć się znakiem modułu, klasy lub struktury zawierającej element docelowy. Każdy element w ścieżce musi zawierać element, który po nim następuje.  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3.  Przygotowanie ciągu kwalifikacji do elementu docelowego. Umieść okres (`.`) po każdego elementu w ścieżce. Aplikacja musi mieć dostęp do każdego elementu w ciągu kwalifikacji.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  Napisz wyrażenie lub instrukcję przypisania odwołujące się do elementu docelowego w normalny sposób.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  Poprzedź nazwę elementu docelowego przy użyciu parametrów kwalifikacji. Nazwę należy natychmiast po kropce (`.`) następujący modułu, klasy lub struktury, który zawiera element.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  Kompilator używa ciągu kwalifikacji, aby znaleźć Wyczyść, jednoznaczną deklaracji, do którego może odnosić odwołanie do elementu docelowego.  
  
 Może być również konieczne kwalifikują się odwołania do nazwy, jeśli aplikacja ma dostęp do więcej niż jeden element programowania, który ma taką samą nazwę. Na przykład <xref:System.Windows.Forms> i <xref:System.Web.UI.WebControls> przestrzenie nazw obu zawierają `Label` klasy (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> i <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>). Jeśli aplikacja korzysta z obu lub definiuje swój własny `Label` klasy, należy odróżnić poszczególne `Label` obiektów. Uwzględnij aliasu przestrzeni nazw lub importu w deklaracji zmiennej. W poniższym przykładzie użyto aliasu importu.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Inne elementy zawierające elementy członkowskie  
 Gdy używasz nieudostępnionych członkiem innej klasy lub struktury, należy najpierw kwalifikujesz się do nazwy elementu członkowskiego za pomocą zmiennej lub wyrażenia, który wskazuje na wystąpienie klasy lub struktury. W poniższym przykładzie `demoClass` jest wystąpieniem klasy o nazwie `class1`.  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 Sama nazwa klasy nie można użyć, aby zakwalifikować się elementu członkowskiego, który nie jest [Shared](../../../../visual-basic/language-reference/modifiers/shared.md). Należy najpierw utworzyć wystąpienia w zmiennej obiektu (w tym przypadku `demoClass`), a następnie Odwołaj przez nazwę zmiennej.  
  
 Jeśli klasa lub struktura ma `Shared` elementu członkowskiego, może kwalifikujesz się do tego elementu członkowskiego o nazwie klasy lub struktury lub za pomocą zmiennej lub wyrażenia, który wskazuje na wystąpienie.  
  
 Moduł nie ma wszelkie osobnych wystąpień, a jej elementy członkowskie są `Shared` domyślnie. W związku z tym kwalifikujesz się do członka modułu z nazwą modułu.  
  
 Poniższy przykład pokazuje kwalifikowanego odwołania do procedur element członkowski modułu. Przykład deklaruje dwie `Sub` procedur, o nazwie `perform`, w różnych modułach w projekcie. Każdy z nich mogą zostać określone bez kwalifikacji w ramach własnego modułu, ale musi być kwalifikowana, jeśli przywoływane z dowolnego miejsca. Ponieważ końcowe odwoływać w `module3` nie kwalifikuje się `perform`, kompilator nie można rozpoznać tego odwołania.  
  
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
 Do użycia [publicznych](../../../../visual-basic/language-reference/modifiers/public.md) elementy zdefiniowane w innym projekcie, należy najpierw ustawić *odwołania* do tego projektu zestawu lub biblioteka typów. Aby ustawić odwołanie, kliknij **Dodaj odwołanie** na **projektu** menu lub użyj [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) — opcja kompilatora wiersza polecenia.  
  
 Na przykład, można użyć modelu obiektów XML z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Jeśli odwołanie jest ustawiona na <xref:System.Xml> przestrzeni nazw, można zadeklarować i użyć dowolnego z jego klas, takie jak <xref:System.Xml.XmlDocument>. W poniższym przykładzie użyto <xref:System.Xml.XmlDocument>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Importowanie zawierający elementy  
 Możesz użyć [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do *zaimportować* przestrzenie nazw, które zawierają moduły lub klasy, które chcesz użyć. Dzięki temu można odwoływać się do elementów zdefiniowanych w importowanych przestrzeni nazw bez w pełni kwalifikowania ich nazwy. Poniższy przykład ponownie zapisuje poprzedniego przykładu, aby zaimportować <xref:System.Xml> przestrzeni nazw.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 Ponadto `Imports` instrukcji można zdefiniować *zaimportować alias* dla każdej importowanych przestrzeni nazw. Dzięki temu może być krótsze i bardziej czytelny kod źródłowy. Poniższy przykład ponownie zapisuje poprzedniego przykładu, aby użyć `xD` jako alias <xref:System.Xml> przestrzeni nazw.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 `Imports` Instrukcji nie udostępnia elementy z innych projektów do swojej aplikacji. Oznacza to, że nie przyjmuje miejsce odwołanie do ustawienia. Importowanie przestrzeni nazw, po prostu usuwa wymaganie, aby kwalifikowania nazwy zdefiniowane w tej przestrzeni nazw.  
  
 Można również użyć `Imports` instrukcję, aby zaimportować moduły, klasy, struktury i wyliczenia. Następnie można użyć elementów członkowskich takich zaimportowane elementy bez kwalifikacji. Jednak zawsze musi kwalifikować nieudostępnionych członków klasy i struktury za pomocą zmiennej lub wyrażenia, które ocenia do wystąpienia klasy lub struktury.  
  
## <a name="naming-guidelines"></a>Wskazówki dotyczące nazewnictwa  
 Po zdefiniowaniu dwóch lub więcej elementów programowania, które mają taką samą nazwę *nazwę niejednoznaczności* może spowodować, gdy kompilator próbuje rozpoznać odwołania do tej nazwy. Jeśli więcej niż jedną definicję znajduje się w zakresie lub Brak definicji znajduje się w zakresie, odwołanie jest nierozwiązywalny. Aby uzyskać przykład zobacz "Przykład kwalifikowana" na tej stronie pomocy.  
  
 Aby uniknąć niejednoznaczności, należy zapewniając wszystkie swoje elementy unikatowe nazwy. Następnie można tworzyć odwołania do dowolnego elementu bez potrzeby kwalifikowania nazwy przestrzeni nazw, modułu lub klasy. Możesz też zmniejszyć prawdopodobieństwo przypadkowego odwołujące się do niewłaściwej elementu.  
  
## <a name="shadowing"></a>Przesłanianie  
 Gdy dwa elementy programowania mają taką samą nazwę, jeden z nich można ukryć, lub *w tle*, jeden z nich. Tekst z cieniem element nie jest dostępne do użytku; Zamiast tego po kodzie używa nazwy elementu zasłonięte, kompilator Visual Basic jest rozpoznawany jako jego przesłaniania elementu. Aby uzyskać bardziej szczegółowy opis wraz z przykładami, zobacz [przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
 [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Operator New](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)
