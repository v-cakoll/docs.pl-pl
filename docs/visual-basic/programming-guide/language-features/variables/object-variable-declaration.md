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
ms.openlocfilehash: f5f77b81380d997e078a9f52ac4aae6f6e975575
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656285"
---
# <a name="object-variable-declaration-visual-basic"></a>Deklaracja zmiennej obiektu (Visual Basic)
Instrukcja deklaracji normalne umożliwia deklarowanie zmiennej obiektu. Dla typu danych, należy określić albo `Object` (to znaczy [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)) lub więcej określonej klasy, z którego ma być utworzony obiekt.  
  
 Deklarowanie zmiennej jako `Object` jest taka sama jak deklarowanie go jako <xref:System.Object?displayProperty=nameWithType>.  
  
 Deklaracja zmiennej z konkretnego obiektu klasy dostępne wszystkie metody i właściwości udostępniane przez tę klasę i klasy, z których dziedziczy. Deklarowanie zmiennej o <xref:System.Object>, może uzyskać dostęp tylko do elementów członkowskich z <xref:System.Object> klasy, chyba że włączenie `Option Strict Off` umożliwia późne powiązania.  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Deklarowanie zmiennej obiektu, należy użyć następującej składni:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Można również określić [publicznego](../../../../visual-basic/language-reference/modifiers/public.md), [chronione](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, [prywatnej](../../../../visual-basic/language-reference/modifiers/private.md), [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), lub [statycznych](../../../../visual-basic/language-reference/modifiers/static.md) w deklaracji. Następujące deklaracje przykładzie są prawidłowe:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Późne wiązanie i wczesne powiązania  
 Czasami określonej klasy jest nieznany, dopóki działania kodu. W takim przypadku należy zadeklarować zmienną obiektu o `Object` — typ danych. Spowoduje to utworzenie ogólne odwołanie do dowolnego typu obiektu i określonej klasy jest przypisana w czasie wykonywania. Ta metoda jest wywoływana *późne wiązanie*. Późne wiązanie wymaga dodatkowego czasu wykonywania. Ogranicza kod do metody i właściwości klas, które ostatnio zostały przypisane do niego. Może to powodować błędy środowiska wykonawczego, jeśli kod spróbuje dostęp do elementów członkowskich innej klasy.  
  
 Gdy znasz określonej klasy w czasie kompilacji, powinny deklarować zmienna obiektu, należy dla tej klasy. Ta metoda jest wywoływana *wczesne wiązanie*. Wczesne powiązania poprawia wydajność i zapewnia dostęp kod do metody i właściwości określonej klasy. W poprzednich deklaracjach przykład, gdy zmienna `objA` używa tylko obiektów klasy <xref:System.Windows.Forms.Label?displayProperty=nameWithType>, należy określić `As System.Windows.Forms.Label` w jego deklaracji.  
  
### <a name="advantages-of-early-binding"></a>Zalety wczesne powiązania  
 Deklarowanie zmiennej obiektu jako określonej klasy zapewnia kilka korzyści:  
  
-   Sprawdzanie typu automatyczne  
  
-   Zapewniony dostęp do wszystkich członków określonej klasy  
  
-   Obsługa Microsoft IntelliSense w edytorze kodu  
  
-   Ulepszona czytelność kodu  
  
-   Mniejszą liczbę błędów w kodzie  
  
-   Błędy przechwycono na czas kompilacji, a nie czas wykonywania  
  
-   Szybsze wykonywanie kodu  
  
## <a name="access-to-object-variable-members"></a>Dostęp do członków zmiennej obiektu  
 Gdy `Option Strict` włączono `On`, zmienna obiektu można uzyskać dostęp tylko metody i właściwości klasy, z którym należy zadeklarować. Ilustruje to poniższy przykład.  
  
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
  
 W tym przykładzie `p` można używać tylko członkowie <xref:System.Object> klasy, które nie obejmują `Left` właściwości. Z drugiej strony `q` został zadeklarowany jako typ <xref:System.Windows.Forms.Label>, dlatego można używać metod i właściwości <xref:System.Windows.Forms.Label> klasy w <xref:System.Windows.Forms> przestrzeni nazw.  
  
## <a name="flexibility-of-object-variables"></a>Elastyczność zmienne obiektów  
 Podczas pracy z obiektów w hierarchii dziedziczenia, masz do wyboru klasy, które do użycia na potrzeby deklarowania zmiennych obiektu. Do zgłoszenia tego wyboru, należy uwzględnić elastyczność przypisanie obiektu przed dostępem do członków klasy. Rozważmy na przykład hierarchii dziedziczenia, który prowadzi do <xref:System.Windows.Forms.Form?displayProperty=nameWithType> klasy:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Załóżmy, że aplikacja definiuje klasy formularza o nazwie `specialForm`, który dziedziczy z klasy <xref:System.Windows.Forms.Form>. Można zadeklarować zmiennej obiektu, który odwołuje się specjalnie do `specialForm`, jak pokazano na poniższym przykładzie.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 Deklaracja w poprzednim przykładzie ogranicza zmiennej `nextForm` do obiektów klasy `specialForm`, ale również zapewnia wszystkie metody i właściwości `specialForm` dostępne dla `nextForm`, jak również ze wszystkimi członkami wszystkie klasy, z którego `specialForm` dziedziczy.  
  
 Zmienna obiektu bardziej ogólne ułatwia ona typu <xref:System.Windows.Forms.Form>, jak pokazano na poniższym przykładzie.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 Deklaracja w poprzednim przykładzie można przypisać wszystkie formularza w aplikacji `anyForm`. Jednak mimo że `anyForm` mogą uzyskiwać dostęp do wszystkich elementów członkowskich klasy <xref:System.Windows.Forms.Form>, nie może używać dodatkowych metod i właściwości zdefiniowane dla określonych formularzy, takie jak `specialForm`.  
  
 Wszystkie elementy członkowskie klasy podstawowej są dostępne dla klasy pochodnej, ale dodatkowe elementy członkowskie klasy pochodnej są niedostępne dla klasy podstawowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do niego w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [Instrukcje: dostęp do elementów członkowskich obiektu](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [Operator New](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
