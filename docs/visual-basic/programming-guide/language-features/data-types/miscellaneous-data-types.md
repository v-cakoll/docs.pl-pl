---
title: Różne typy danych (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 9261a02f3dc286dc37b3073158ccc0c151030fe0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="miscellaneous-data-types-visual-basic"></a>Różne typy danych (Visual Basic)
Visual Basic dostarcza kilku typów danych, które nie są zorientowanych w kierunku cyfr lub znaków. Zamiast tego mają do czynienia specjalne dane takie jak tak/nie wartości, wartości daty/godziny i adresy obiektu.  
  
 Aby uzyskać tabelę przedstawiającą porównanie side-by-side typy danych Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="boolean-type"></a>Typ Boolean  
 [— Typ danych logicznych](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) jest wartość bez znaku, który jest interpretowany jako `True` lub `False`. Szerokość danych zależy od platformy implementującej. Jeśli zmienna może zawierać tylko dwa wartości, takie jak PRAWDA/FAŁSZ tak/nie lub Włącz/Wyłącz, Zadeklaruj ją jako `Boolean`.  
  
## <a name="date-type"></a>Date — typ  
 [Date — typ danych](../../../../visual-basic/language-reference/data-types/date-data-type.md) jest wartością 64-bitowego, która przechowuje informacje zarówno datę i godzinę. Jednostka reprezentuje 100 nanosekundach czas, który upłynął od początku (00:00:00) 1 stycznia 1 rok kalendarza gregoriańskiego. Jeśli zmienna może zawierać wartości daty i godziny, Zadeklaruj ją jako `Date`.  
  
## <a name="object-type"></a>Typ obiektu  
 [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md) jest 32-bitowy adres, który wskazuje na wystąpienie obiektu w aplikacji lub w innej aplikacji. `Object` Zmiennej może odwoływać się do dowolnego obiektu aplikacja rozpoznaje lub danych dowolnego typu danych. Dotyczy to zarówno *typów wartości*, takich jak `Integer`, `Boolean`i wystąpienia struktury i *typy referencyjne*, które są wystąpienia obiektów, takich jak utworzone na podstawie klasy `String`i <xref:System.Windows.Forms.Form>, a tablica wystąpień.  
  
 Jeśli zmienna przechowuje wskaźnik do wystąpienia klasy, która nie wiadomo, w czasie kompilacji lub dane różnych typów danych może wskazywać, Zadeklaruj ją jako `Object`.  
  
 Zaletą `Object` — typ danych jest, że można użyć go do przechowywania danych dowolnego typu danych. Wadą jest pociągnąć za sobą dodatkowe operacje zająć więcej czasu wykonywania i zwiększyć bezpieczeństwo aplikacji działać wolniej. Jeśli używasz `Object` ponieść zmiennej dla typów wartości, *boxing* i *rozpakowującej*. Jeśli używasz dla typów odwołań ponosisz *późne wiązanie*.  
  
## <a name="see-also"></a>Zobacz też  
 [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Typy danych liczbowych](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [Znakowe typy danych](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Wczesne i późne powiązania](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
