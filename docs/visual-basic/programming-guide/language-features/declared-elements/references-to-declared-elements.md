---
title: Odwołania do elementów zadeklarowanych (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic]
- references [Visual Basic], declared elements
- qualified names [Visual Basic]
ms.assetid: d6301709-f4cc-4b7a-b8ba-80898f14ab46
ms.openlocfilehash: 18f9920891e35517efe7adcfd4c03e03ac771478
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655814"
---
# <a name="references-to-declared-elements-visual-basic"></a>Odwołania do elementów zadeklarowanych (Visual Basic)
Gdy kod odwołuje się do elementu zadeklarowane, kompilator Visual Basic jest zgodna z nazwą w odwołania do odpowiednich deklaracja o takiej nazwie. Jeśli więcej niż jeden element jest zadeklarowany jako o takiej samej nazwie, można kontrolować, które z tych elementów jest wykorzystanie przez *kwalifikującego* jego nazwy.  
  
 Kompilator próbuje dopasować nazwę odwołania do nazwy deklaracji z *najwęższy zakres*. Oznacza to, rozpoczyna się od kodu odniesienia i działa na zewnątrz przez kolejne poziomy zawierający elementy.  
  
 W poniższym przykładzie przedstawiono odwołania do dwóch zmiennych o takiej samej nazwie. Przykład deklaruje dwie zmienne, każdy o nazwie `totalCount`, na różnych poziomach zakresu w module `container`. Jeśli procedura `showCount` Wyświetla `totalCount` bez kwalifikacji, kompilator Visual Basic Usuwa odwołanie do deklaracja o zakresie najwęższym, czyli deklaracji lokalnej wewnątrz `showCount`. Gdy kwalifikuje się `totalCount` z modułem zawierającego `container`, kompilator usuwa odwołanie do deklaracji w szerszym zakresie.  
  
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
 Jeśli chcesz zastąpić ten proces wyszukiwania i określić nazwę zadeklarowany w szerszy zakres, należy najpierw *zakwalifikować* nazwy za pomocą elementu zawierającego szerszego zakresu. W niektórych przypadkach może być również konieczne zakwalifikować zawierającego element.  
  
 Kwalifikowanie oznacza nazwę, poprzedzającym go w instrukcji źródła informacje określające, w którym zdefiniowana jest elementem docelowym. Te informacje jest nazywany *ciąg kwalifikacji*. Może zawierać jeden lub więcej przestrzeni nazw i modułu, klasy lub struktury.  
  
 Ciąg kwalifikacji jednoznacznie określić modułu, klasy lub struktury zawierającej element docelowy. Kontener z kolei może znajdować się w innego elementu zawierającego zwykle przestrzeni nazw. Konieczne może zawierać wielu elementów zawierających w ciągu kwalifikacji.  
  
#### <a name="to-access-a-declared-element-by-qualifying-its-name"></a>Dostęp do elementu zadeklarowane przy kwalifikujących się jego nazwę  
  
1.  Określ lokalizację, w którym element został zdefiniowany. Może to obejmować przestrzeni nazw lub nawet hierarchii przestrzeni nazw. W obszarze nazw najniższego poziomu elementu muszą być zawarte w module, klasy lub struktury.  
  
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
  
2.  Określ ścieżkę kwalifikacji na podstawie lokalizacji elementu docelowego. Rozpoczynać się od przestrzeni nazw najwyższego poziomu, przejdź do obszaru nazw najniższym poziomie, a kończyć modułu, klasy lub struktury zawierającej element docelowy. Każdy element ścieżki musi zawierać element, do którego następuje.  
  
     `outerSpace` → `innerSpace` → `holdsTotals` → `totals`  
  
3.  Przygotuj kwalifikacji ciągu dla elementu docelowego. Umieść okres (`.`) po każdym elementem w ścieżce. Aplikacja musi mieć dostęp do każdego elementu w ciągu kwalifikacji.  
  
    ```vb  
    outerSpace.innerSpace.holdsTotals.totals.  
    ```  
  
4.  Napisz wyrażenia lub instrukcji odwołujących się do elementu docelowego w zwykły sposób.  
  
    ```vb  
    grandTotal = 9000  
    ```  
  
5.  Poprzedź nazwę elementu docelowego z ciągiem kwalifikacji. Nazwę należy natychmiast po kropce (`.`) następujący modułu, klasy lub struktury, który zawiera element.  
  
    ```vb  
    ' Assume the following module is part of your code.  
    Module accessGrandTotal  
        Public Sub setGrandTotal()  
            outerSpace.innerSpace.holdsTotals.totals.grandTotal = 9000  
        End Sub  
    End Module  
    ```  
  
6.  Kompilator używa ciągu kwalifikacji można znaleźć Wyczyść, jednoznaczne deklaracji, do której może dopasować odwołanie do elementu docelowego.  
  
 Należy również kwalifikują się odwołania do nazwy, jeśli aplikacja ma dostęp do więcej niż jeden element programowania, który ma taką samą nazwę. Na przykład <xref:System.Windows.Forms> i <xref:System.Web.UI.WebControls> nazw obu zawierają `Label` klasy (<xref:System.Windows.Forms.Label?displayProperty=nameWithType> i <xref:System.Web.UI.WebControls.Label?displayProperty=nameWithType>). Jeśli aplikacja używa zarówno lub definiuje własną `Label` klasy, należy odróżnić różnych `Label` obiektów. Alias przestrzeni nazw lub importu należy uwzględnić w deklaracji zmiennej. W poniższym przykładzie użyto aliasu importu.  
  
```vb  
' The following statement must precede all your declarations.  
Imports win = System.Windows.Forms, web = System.Web.UI.WebControls  
' The following statement references the Windows.Forms.Label class.  
Dim winLabel As New win.Label()  
```  
  
## <a name="members-of-other-containing-elements"></a>Elementy członkowskie innych elementów zawierających  
 Użycie jest udostępniana członkiem innej klasy lub struktury, należy najpierw zakwalifikować nazwę elementu członkowskiego z zmiennej lub wyrażenie, które wskazuje na wystąpienie klasy lub struktury. W poniższym przykładzie `demoClass` jest wystąpieniem klasy o nazwie `class1`.  
  
```vb  
Dim demoClass As class1 = New class1()  
demoClass.someSub[(argumentlist)]  
```  
  
 Nazwa klasy nie można użyć, aby zakwalifikować elementu członkowskiego, który nie jest [Shared](../../../../visual-basic/language-reference/modifiers/shared.md). Należy najpierw utworzyć wystąpienia w zmiennej obiektu (w tym przypadku `demoClass`), a następnie odwołania przez nazwę zmiennej.  
  
 Jeśli ma klasę lub strukturę `Shared` elementu członkowskiego, możesz skorzystać ten element członkowski o nazwie klasy lub struktury lub za pomocą zmiennej lub wyrażenie wskazujące wystąpienie.  
  
 Moduł nie ma żadnych osobnych wystąpień i jej elementów członkowskich są `Shared` domyślnie. Dlatego możesz skorzystać z elementem członkowskim modułu o nazwie modułu.  
  
 W poniższym przykładzie przedstawiono kwalifikowanego odwołania do modułu Członkowskie procedur. Przykład deklaruje dwa `Sub` procedur, o nazwie `perform`, w różnych modułach w projekcie. Każdej z nich można określić bez kwalifikacji własnego modułu, ale musi być kwalifikowana, jeśli przywoływany w innym miejscu. Ponieważ odwoływał się w końcowym `module3` nie kwalifikuje się `perform`, kompilator nie można rozpoznać tego odwołania.  
  
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
 Aby użyć [publicznego](../../../../visual-basic/language-reference/modifiers/public.md) elementy zdefiniowane w innym projekcie, należy najpierw ustawić *odwołania* do tego projektu biblioteki zestawu lub typu. Aby ustawić odwołanie, kliknij przycisk **Dodaj odwołanie** na **projektu** menu lub użyj [/Reference (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/reference.md) — opcja kompilatora wiersza polecenia.  
  
 Na przykład można użyć modelu obiektów XML z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Jeśli ustawisz odwołanie <xref:System.Xml> przestrzeni nazw, można zadeklarować i użyć żadnej z jej klas, takich jak <xref:System.Xml.XmlDocument>. W poniższym przykładzie użyto <xref:System.Xml.XmlDocument>.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As System.Xml.XmlDocument  
```  
  
## <a name="importing-containing-elements"></a>Importowanie elementów zawierających  
 Można użyć [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do *zaimportować* przestrzenie nazw, które zawierają moduły lub klasy, które chcesz użyć. Dzięki temu można odwoływać się do elementów zdefiniowanych w zaimportowaną przestrzenią nazw bez pełni kwalifikujących się ich nazw. Poniższy przykład ponownie zapisuje poprzedni przykład, aby zaimportować <xref:System.Xml> przestrzeni nazw.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As XmlDocument  
```  
  
 Ponadto `Imports` instrukcji można zdefiniować *zaimportować alias* dla każdej importowanych przestrzeni nazw. Ułatwia to kodu źródłowego, krótsze i łatwiejsze do odczytu. Poniższy przykład ponownie zapisuje poprzedni przykład, aby użyć `xD` jako alias <xref:System.Xml> przestrzeni nazw.  
  
```vb  
' Assume this project has a reference to System.Xml  
' The following statement must precede all your declarations.  
Imports xD = System.Xml  
' The following statement creates xDoc as an XML document object.  
Dim xDoc As xD.XmlDocument  
```  
  
 `Imports` Instrukcji nie udostępnić elementy z innych projektów do aplikacji. Oznacza to, że nie przyjmuje ustawienie odwołanie miejsca. Importowanie przestrzeni nazw, po prostu eliminuje konieczność na kwalifikować się zdefiniowanych w tej przestrzeni nazw.  
  
 Można również użyć `Imports` instrukcji, aby zaimportować moduły, klas, struktur i wyliczenia. Następnie można członkami takich importowanych elementów bez kwalifikacji. Jednak należy zawsze zakwalifikować udostępniana elementów członkowskich klas i struktur za pomocą zmiennej lub wyrażenie obliczane do wystąpienia klasy lub struktury.  
  
## <a name="naming-guidelines"></a>Zasady nazewnictwa  
 Podczas definiowania co najmniej dwa elementy programowania, które mają taką samą nazwę, *nazwa niejednoznaczności* może występować, gdy kompilator próbuje rozpoznać odwołania do tej nazwy. Jeśli więcej niż jedną definicję znajduje się w zakresie lub jeśli definicja nie znajduje się w zakresie, odwołanie jest nierozwiązywalne. Na przykład zobacz "Przykład odwołania do kwalifikowanego" na tej stronie pomocy.  
  
 Można uniknąć niejednoznaczności, zapewniając wszystkich elementów unikatowe nazwy. Następnie możesz wprowadzić odwołanie do każdego elementu bez konieczności jego nazwy z przestrzeni nazw, modułu lub klasy. Można także zmniejszyć ryzyko przypadkowego odwołujące się do niewłaściwego elementu.  
  
## <a name="shadowing"></a>Przesłanianie  
 Gdy dwa elementy programowania o tej samej nazwie, jeden z nich można ukryć, lub *tle*, jeden z nich. Zasłonięty element jest niedostępny dla odwołania; Zamiast tego po kodzie używa nazwy elementu zasłonięty, kompilator Visual Basic rozpoznaje ją do przesłaniania elementu. Aby uzyskać bardziej szczegółowy opis wraz z przykładami, zobacz [przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
 [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Imports, instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [Operator New](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)
