---
title: 'Porady: dostęp do elementów członkowskich obiektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: 62be2955bd1f62fa5af4e54fb0af5e7dca29c421
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Porady: dostęp do elementów członkowskich obiektu (Visual Basic)
Jeśli masz zmiennej obiektu, który odwołuje się do obiektu często chcesz pracować z elementami członkowskimi tego obiektu, takie jak metod, właściwości, pól i zdarzeń. Na przykład po utworzeniu nowego <xref:System.Windows.Forms.Form> obiektu, należy ustawić jej <xref:System.Windows.Forms.Control.Text%2A> właściwość lub wywołanie jego <xref:System.Windows.Forms.Control.Focus%2A> metody.  
  
## <a name="accessing-members"></a>Uzyskiwanie dostępu do elementów członkowskich  
 Za pomocą zmiennej, która odwołuje się do niego dostęp do elementów członkowskich obiektu.  
  
#### <a name="to-access-members-of-an-object"></a>Aby uzyskać dostępu do elementów członkowskich obiektu  
  
-   Użycie operatora dostępu do elementu członkowskiego (`.`) między nazwą zmiennej obiektu i nazwę elementu członkowskiego.  
  
    ```  
    currentText = newForm.Text  
    ```  
  
     Jeśli element członkowski jest [Shared](../../../../visual-basic/language-reference/modifiers/shared.md), nie trzeba zmienną do niego dostęp.  
  
## <a name="accessing-members-of-an-object-of-known-type"></a>Uzyskiwanie dostępu do elementów członkowskich obiektu znanego typu  
 Jeśli w czasie kompilacji jest znany typ obiektu, możesz użyć *wczesne wiązanie* zmiennej, która odwołuje się do niego.  
  
#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Aby dostęp do elementów członkowskich obiektu, dla którego znany typ w czasie kompilacji  
  
1.  Deklarowanie zmiennej obiektu typu obiektu, który chcesz przypisać do zmiennej.  
  
    ```  
    Dim extraForm As System.Windows.Forms.Form  
    ```  
  
     Z `Option Strict On`, można przypisać tylko <xref:System.Windows.Forms.Form> obiektów (lub obiektów typu pochodzącego od <xref:System.Windows.Forms.Form>) do `extraForm`. Jeśli zdefiniowano klasy lub struktury z rozszerzanie `CType` konwersji do <xref:System.Windows.Forms.Form>, można również przypisać tej klasy lub struktury do `extraForm`.  
  
2.  Użycie operatora dostępu do elementu członkowskiego (`.`) między nazwą zmiennej obiektu i nazwę elementu członkowskiego.  
  
    ```  
    extraForm.Show()  
    ```  
  
     Uzyskiwać dostęp do wszystkich metod i właściwości specyficzne dla <xref:System.Windows.Forms.Form> klasy, niezależnie od tego, co `Option Strict` to ustawienie.  
  
## <a name="accessing-members-of-an-object-of-unknown-type"></a>Uzyskiwanie dostępu do elementów członkowskich obiektu nieznanego typu.  
 Jeśli nie znasz typu obiektu w czasie kompilacji, należy użyć *późne wiązanie* dla dowolnej zmiennej, która odwołuje się do niego.  
  
#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Aby dostęp do elementów członkowskich obiektu, dla których nie wiadomo, typ w czasie kompilacji  
  
1.  Deklarowanie zmiennej obiektu za [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md). (Deklarowanie zmiennej jako `Object` jest taka sama jak deklarowanie go jako <xref:System.Object?displayProperty=nameWithType>.)  
  
    ```  
    Dim someControl As Object  
    ```  
  
     Z `Option Strict On`, można uzyskać dostęp tylko do elementów członkowskich, które są zdefiniowane na <xref:System.Object> klasy.  
  
2.  Użycie operatora dostępu do elementu członkowskiego (`.`) między nazwą zmiennej obiektu i nazwę elementu członkowskiego.  
  
    ```  
    someControl.GetType()  
    ```  
  
     Aby można było uzyskać dostępu do elementów członkowskich obiektu przypisanie zmiennej obiektu, należy ustawić `Option Strict Off`. Gdy to zrobisz, kompilator nie może zagwarantować, że dany element jest udostępniana przez obiekt, który można przypisać do zmiennej. Jeśli obiekt nie ujawnia członka próbie uzyskania dostępu, <xref:System.MemberAccessException> Wystąpił wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Object>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.MemberAccessException>  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Option Strict, instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
