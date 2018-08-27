---
title: Różne typy danych (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 490a462859a916d21c816ff96c47d2deeb9312ee
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931141"
---
# <a name="miscellaneous-data-types-visual-basic"></a>Różne typy danych (Visual Basic)
Visual Basic dostarcza kilka typów danych, które nie są opracowane głównie pod kątem liczby lub znaki. Zamiast tego mają do czynienia wyspecjalizowane danych takich jak tak/nie wartości, wartości daty/godziny i adresy obiektów.  
  
 Aby uzyskać tabelę przedstawiającą porównanie side-by-side typy danych Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="boolean-type"></a>Typ wartości logicznej  
 [Typ danych Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) jest wartością bez znaku, który jest interpretowany jako `True` lub `False`. Szerokość danych zależy od platformy implementującej. Jeśli zmienna może zawierać tylko dwoma stanami wartości, takich jak PRAWDA/FAŁSZ, tak/nie lub włączenia/wyłączenia, Zadeklaruj go jako `Boolean`.  
  
## <a name="date-type"></a>Date — typ  
 [Date — typ danych](../../../../visual-basic/language-reference/data-types/date-data-type.md) jest wartość 64-bitową, która przechowuje informacje daty i godziny. Każdy przyrost reprezentuje 100 nanosekund czas, który upłynął od początku (12:00 AM) od 1 stycznia 1 roku w kalendarzu gregoriańskim. Jeśli zmienna może zawierać wartość typu date i/lub wartość czasu, Zadeklaruj go jako `Date`.  
  
## <a name="object-type"></a>Typ obiektu  
 [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md) jest 32-bitowy adres, który wskazuje na wystąpienie obiektu w aplikacji lub w innej aplikacji. `Object` Zmiennej może odwoływać się do dowolnego obiektu, aplikacja rozpoznaje lub danymi dowolnego typu danych. Dotyczy to zarówno *typy wartości*, takich jak `Integer`, `Boolean`i wystąpienia struktury i *typy odwołań*, służą do wystąpienia obiektów, utworzone na podstawie klasy takie jak `String`i <xref:System.Windows.Forms.Form>, a tablica wystąpień.  
  
 Jeśli zmienna przechowuje wskaźnik do wystąpienia klasy, która nie wiesz, w czasie kompilacji lub może wskazywać danych różnych typów danych, Zadeklaruj go jako `Object`.  
  
 Zaletą `Object` typ danych jest, że służy do przechowywania danych dowolnego typu danych. Wadą jest to pociągnąć za sobą dodatkowych operacji, które zająć więcej czasu wykonywania i aplikacja działać wolniej. Jeśli używasz `Object` zmiennej dla typów wartości, wiąże się z *pakowania* i *Rozpakowywanie*. Jeśli używasz dla typów odwołań wiąże się z *późnym wiązaniu*.  
  
## <a name="see-also"></a>Zobacz też  
 [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Typy danych liczbowych](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [Znakowe typy danych](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Wczesne i późne powiązania](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
