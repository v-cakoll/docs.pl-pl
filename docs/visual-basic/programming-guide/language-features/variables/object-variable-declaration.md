---
title: Deklaracja zmiennej obiektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: 9e57d49965537a45bc62b9078079389efcfb2e2c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598746"
---
# <a name="object-variable-declaration-visual-basic"></a>Deklaracja zmiennej obiektu (Visual Basic)
Instrukcji deklaracji normalne umożliwiają deklarowanie zmiennej obiektu. Dla typu danych, należy określić albo `Object` (czyli [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)) lub dokładniej klasy, z którego ma zostać utworzony obiekt.  
  
 Deklarowanie zmiennej jako `Object` jest taka sama jak deklarowania go jako <xref:System.Object?displayProperty=nameWithType>.  
  
 Kiedy Deklarujesz zmienną za pomocą konkretnego obiektu klasy, można uzyskać dostęp do, wszystkie metody i właściwości udostępniane przez tę klasę i klasy, z których dziedziczy. Przy deklarowaniu zmiennej <xref:System.Object>, może uzyskać dostęp tylko członkowie <xref:System.Object> klasy, o ile nie wyłączysz `Option Strict Off` umożliwia późnego wiązania.  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Aby zadeklarować zmienną obiektu, należy użyć następującej składni:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Można również określić [publicznych](../../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), lub [statyczne](../../../../visual-basic/language-reference/modifiers/static.md) w deklaracji. Następujące deklaracje przykład są prawidłowe:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Późne wiązanie i wczesne powiązania  
 Czasami określonej klasy jest nieznany, dopóki kod jest wykonywany. W takim przypadku należy zadeklarować zmienną obiektu za pomocą `Object` — typ danych. Spowoduje to utworzenie ogólne odwołanie do dowolnego typu obiektu i określonej klasy są przypisywane w czasie wykonywania. Jest to nazywane *późnym wiązaniu*. Późne wiązanie wymaga dodatkowego czasu wykonywania. Ogranicza kod do metody i właściwości klas, które ostatnio zostały przypisane do niego. Może to spowodować błędy czasu wykonywania, jeśli kod próbuje dostęp do elementów członkowskich innej klasy.  
  
 Gdy znasz konkretną klasę w czasie kompilacji, należy zadeklarować zmienną obiektu tej klasy. Jest to nazywane *wczesne powiązania*. Wczesne powiązania zapewnia lepszą wydajność i gwarantuje dostęp kod do metody i właściwości określonej klasy. W poprzedniej deklaracji przykład, gdy zmienna `objA` używa tylko obiekty klasy <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, należy określić `As System.Windows.Forms.Label` w jego deklaracji.  
  
### <a name="advantages-of-early-binding"></a>Korzyści wynikające z wczesne powiązania  
 Deklarowanie zmiennej obiektu jako określoną klasę zapewnia kilka korzyści:  
  
- Kontrola typów automatyczne  
  
- Zapewniony dostęp do wszystkich elementów członkowskich określonej klasy  
  
- Obsługa Microsoft IntelliSense w edytorze kodu  
  
- Lepszej czytelności kodu  
  
- Mniej błędów w kodzie  
  
- Błędy wyłapywane w czas kompilacji, a nie czasu wykonywania  
  
- Szybsze wykonywanie kodu  
  
## <a name="access-to-object-variable-members"></a>Dostęp do obiektu zmiennych składowych  
 Gdy `Option Strict` włączeniu `On`, zmienna obiektu dostęp do metod i właściwości klasy, z którym trzeba je zadeklarować. Ilustruje to poniższy przykład.  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 W tym przykładzie `p` można używać tylko członków <xref:System.Object> klasy, które nie obejmują `Left` właściwości. Z drugiej strony `q` został zadeklarowany jako typ <xref:System.Windows.Forms.Label>, dzięki czemu można użyć wszystkich metod i właściwości <xref:System.Windows.Forms.Label> klasy w <xref:System.Windows.Forms> przestrzeni nazw.  
  
## <a name="flexibility-of-object-variables"></a>Elastyczność zmienne obiektów  
 Podczas pracy z obiektami w hierarchii dziedziczenia, masz do wyboru klasy do deklarowania zmiennych obiektu. Dokonując wyboru, muszą równoważyć elastyczność przypisanie obiektu względem dostępu do składowych klasy. Na przykład, rozważmy Hierarchia dziedziczenia, który prowadzi do <xref:System.Windows.Forms.Form?displayProperty=nameWithType> klasy:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Załóżmy, że aplikacja definiuje klasę formularza o nazwie `specialForm`, który dziedziczy z klasy <xref:System.Windows.Forms.Form>. Można zadeklarować zmienną obiektu, który odwołuje się specjalnie do `specialForm`, jak pokazano w poniższym przykładzie.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 Deklaracji w poprzednim przykładzie ogranicza zmiennej `nextForm` do obiektów klasy `specialForm`, ale on również sprawia, że wszystkie metody i właściwości `specialForm` dostępne dla `nextForm`, jak również jak wszystkie elementy członkowskie wszystkie klasy, z którego `specialForm` dziedziczy.  
  
 Możesz wprowadzić zmienną obiektu bardziej ogólnych, deklarując jej typu <xref:System.Windows.Forms.Form>, jak pokazano w poniższym przykładzie.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 Deklaracja w powyższym przykładzie można przypisać dowolnej formie w aplikacji, aby `anyForm`. Jednak mimo że `anyForm` mogą uzyskiwać dostęp do wszystkich członków klasy <xref:System.Windows.Forms.Form>, nie może używać dowolnych dodatkowe metody lub właściwości, zdefiniowaną dla określonych formularzy, takich jak `specialForm`.  
  
 Wszystkie elementy członkowskie klasy bazowej są dostępne dla klasy pochodnej, ale dodatkowe elementy członkowskie klasy pochodnej jest niedostępny do klasy bazowej.  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Instrukcje: Deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Instrukcje: Dostęp do elementów członkowskich obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [New, operator](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
