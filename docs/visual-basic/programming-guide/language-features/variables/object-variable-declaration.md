---
title: Deklaracja zmiennej obiektu
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
ms.openlocfilehash: b6de52cf738a56a42c82978b54cef31574ab0bcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410364"
---
# <a name="object-variable-declaration-visual-basic"></a>Deklaracja zmiennej obiektu (Visual Basic)
Użyj normalnej instrukcji deklaracji, aby zadeklarować zmienną obiektu. Dla typu danych należy określić wartość `Object` (czyli [Typ danych obiektu](../../../language-reference/data-types/object-data-type.md)) lub bardziej konkretną klasę, z której ma zostać utworzony obiekt.  
  
 Deklarowanie zmiennej jako `Object` takiej samej jak deklarowanie jej jako <xref:System.Object?displayProperty=nameWithType> .  
  
 Po zadeklarowaniu zmiennej z konkretną klasą obiektów, może ona uzyskać dostęp do wszystkich metod i właściwości uwidocznionych przez tę klasę oraz klas, z których ta dziedziczy. Jeśli zmienna jest zadeklarowana przy użyciu <xref:System.Object> , może uzyskać dostęp tylko do elementów członkowskich <xref:System.Object> klasy, chyba że `Option Strict Off` zezwolisz na późne wiązanie.  
  
## <a name="declaration-syntax"></a>Składnia deklaracji  
 Aby zadeklarować zmienną obiektu, użyj następującej składni:  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 Można również określić [Public](../../../language-reference/modifiers/public.md), [Protected](../../../language-reference/modifiers/protected.md), [Friend](../../../language-reference/modifiers/friend.md), `Protected Friend` , [Private](../../../language-reference/modifiers/private.md), [Shared](../../../language-reference/modifiers/shared.md)lub [static](../../../language-reference/modifiers/static.md) w deklaracji. Następujące przykładowe deklaracje są prawidłowe:  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>Późne powiązania i wczesne powiązania  
 Czasami określona Klasa jest nieznana do momentu uruchomienia kodu. W takim przypadku należy zadeklarować zmienną obiektu z `Object` typem danych. Spowoduje to utworzenie ogólnego odwołania do dowolnego typu obiektu, a określona Klasa jest przypisana w czasie wykonywania. Jest to tzw. *późne wiązanie*. Późne wiązanie wymaga dodatkowego czasu wykonania. Ponadto ogranicza kod do metod i właściwości klasy, do której ostatnio przypisano. Może to spowodować błędy w czasie wykonywania, jeśli kod próbuje uzyskać dostęp do elementów członkowskich innej klasy.  
  
 Znając określoną klasę w czasie kompilacji, należy zadeklarować zmienną obiektu jako tej klasy. Nazywa się to *wczesnym wiązaniem*. Wczesne powiązanie zwiększa wydajność i gwarantuje dostęp kodu do wszystkich metod i właściwości konkretnej klasy. W poprzednich przykładowych deklaracjach, jeśli zmienna `objA` używa tylko obiektów klasy <xref:System.Windows.Forms.Label?displayProperty=nameWithType> , należy określić `As System.Windows.Forms.Label` w swojej deklaracji.  
  
### <a name="advantages-of-early-binding"></a>Zalety wczesnego wiązania  
 Deklarowanie zmiennej obiektu jako określonej klasy daje kilka korzyści:  
  
- Automatyczne sprawdzanie typu  
  
- Gwarantowany dostęp do wszystkich elementów członkowskich określonej klasy  
  
- Obsługa technologii IntelliSense firmy Microsoft w edytorze kodu  
  
- Ulepszona czytelność kodu  
  
- Mniejsza liczba błędów w kodzie  
  
- Błędy przechwycone w czasie kompilacji, a nie w czasie wykonywania  
  
- Szybsze wykonywanie kodu  
  
## <a name="access-to-object-variable-members"></a>Dostęp do elementów członkowskich zmiennych obiektu  
 Gdy `Option Strict` jest włączona `On` , zmienna obiektu może uzyskać dostęp tylko do metod i właściwości klasy, z którą ją deklarujesz. Ilustruje to poniższy przykład.  
  
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
  
 W tym przykładzie `p` można używać tylko elementów członkowskich <xref:System.Object> samej klasy, które nie zawierają `Left` właściwości. Z drugiej strony, `q` został zadeklarowany jako typu <xref:System.Windows.Forms.Label> , dlatego może używać wszystkich metod i właściwości <xref:System.Windows.Forms.Label> klasy w <xref:System.Windows.Forms> przestrzeni nazw.  
  
## <a name="flexibility-of-object-variables"></a>Elastyczność zmiennych obiektów  
 Podczas pracy z obiektami w hierarchii dziedziczenia można wybrać klasę, która ma być używana do deklarowania zmiennych obiektu. W przypadku wybrania tego wyboru należy zrównoważyć elastyczność przypisywania obiektów w celu uzyskania dostępu do elementów członkowskich klasy. Rozważmy na przykład hierarchię dziedziczenia prowadzącą do <xref:System.Windows.Forms.Form?displayProperty=nameWithType> klasy:  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 Załóżmy, że aplikacja definiuje klasę formularza o nazwie `specialForm` , która dziedziczy z klasy <xref:System.Windows.Forms.Form> . Można zadeklarować zmienną obiektu, która odwołuje się w `specialForm` odniesieniu do, jak pokazano w poniższym przykładzie.  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 Deklaracja w poprzednim przykładzie ogranicza zmienną `nextForm` do obiektów klasy `specialForm` , ale również udostępnia wszystkie metody i właściwości `specialForm` dostępne dla, a także `nextForm` wszystkie elementy członkowskie wszystkich klas, z których `specialForm` dziedziczy.  
  
 Można sprawić, aby zmienna obiektu była bardziej ogólna przez zadeklarowanie jej jako typu <xref:System.Windows.Forms.Form> , jak pokazano w poniższym przykładzie.  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 Deklaracja w poprzednim przykładzie umożliwia przypisanie dowolnej formy w aplikacji do programu `anyForm` . Jednak chociaż `anyForm` mogą uzyskać dostęp do wszystkich elementów członkowskich klasy <xref:System.Windows.Forms.Form> , nie może używać żadnej z dodatkowych metod lub właściwości zdefiniowanych dla konkretnych formularzy, takich jak `specialForm` .  
  
 Wszystkie elementy członkowskie klasy bazowej są dostępne dla klas pochodnych, ale dodatkowe elementy członkowskie klasy pochodnej są niedostępne dla klasy bazowej.  
  
## <a name="see-also"></a>Zobacz też

- [Zmienne obiektów](object-variables.md)
- [Przypisanie zmiennej obiektu](object-variable-assignment.md)
- [Wartości zmiennej obiektu](object-variable-values.md)
- [Porady: deklarowanie zmiennej obiektu i przydzielanie obiektu do It w Visual Basic](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [Porady: dostęp do elementów członkowskich obiektu](how-to-access-members-of-an-object.md)
- [Operator new](../../../language-reference/operators/new-operator.md)
- [Option Strict — Instrukcja](../../../language-reference/statements/option-strict-statement.md)
- [Wnioskowanie o typie lokalnym](local-type-inference.md)
