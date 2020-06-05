---
title: Zmienna „<variablename>” ukrywa zmienną w otaczającym bloku
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 474a920c9cfdfba7a8157320d9c88b8677958425
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406524"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>Zmienna „\<variablename>” ukrywa zmienną w otaczającym bloku
Zmienna ujęta w bloku ma taką samą nazwę jak inna zmienna lokalna.  
  
 **Identyfikator błędu:** BC30616  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zmień nazwę zmiennej w załączonym bloku, tak aby nie była taka sama jak jakakolwiek inna zmienna lokalna. Przykład:  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- Typową przyczyną tego błędu jest użycie `Catch e As Exception` wewnątrz procedury obsługi zdarzeń. W takim przypadku należy nazwać `Catch` zmienną bloku `ex` zamiast `e` .  
  
- Innym wspólnym źródłem tego błędu jest próba uzyskania dostępu do zmiennej lokalnej zadeklarowanej w `Try` bloku w oddzielnym `Catch` bloku. Aby to poprawić, zadeklaruj zmienną poza `Try...Catch...Finally` strukturą.  
  
## <a name="see-also"></a>Zobacz też

- [Try...Catch...Finally, instrukcja](../statements/try-catch-finally-statement.md)
- [Deklaracja zmiennej](../../programming-guide/language-features/variables/variable-declaration.md)
