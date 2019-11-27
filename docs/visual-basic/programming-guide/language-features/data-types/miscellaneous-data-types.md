---
title: Różne typy danych
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: cc6262b5bb305bb839917e222d831fa3340a1b14
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346336"
---
# <a name="miscellaneous-data-types-visual-basic"></a>Różne typy danych (Visual Basic)
Visual Basic dostarcza kilka typów danych, które nie są zorientowane na numery lub znaki. Zamiast tego zajmują się one wyspecjalizowanymi danymi, takimi jak tak/nie wartości, wartości daty/godziny i adresy obiektów.  
  
 Aby uzyskać tabelę zawierającą porównanie równoległe typów danych Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="boolean-type"></a>Typ wartości logicznej  
 [Typ danych Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) jest wartością bez znaku, która jest interpretowana jako `True` lub `False`. Szerokość danych zależy od platformy implementującej. Jeśli zmienna może zawierać tylko wartości dwustanowe, takie jak true/false, yes/no lub on/off, deklaruj ją jako `Boolean`.  
  
## <a name="date-type"></a>Typ daty  
 [Typ danych Data](../../../../visual-basic/language-reference/data-types/date-data-type.md) jest wartością 64-bitową, która zawiera informacje o dacie i godzinie. Każdy przyrost reprezentuje 100 nanosekund czasu, od momentu rozpoczęcia (12:00 AM) 1 stycznia roku 1 w kalendarzu gregoriańskim. Jeśli zmienna może zawierać wartość typu Date, wartość czasu lub obie te metody, deklaruj ją jako `Date`.  
  
## <a name="object-type"></a>Typ obiektu  
 [Typ danych obiektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) jest adresem 32-bitowym, który wskazuje na wystąpienie obiektu w aplikacji lub w innej aplikacji. Zmienna `Object` może odwoływać się do dowolnego obiektu rozpoznawanego przez aplikację lub do danych dowolnego typu danych. Dotyczy to zarówno *typów wartości*, takich jak `Integer`, `Boolean`i wystąpienia struktury, oraz *typów referencyjnych*, które są wystąpieniami obiektów utworzonych na podstawie klas takich jak `String` i <xref:System.Windows.Forms.Form>i wystąpienia Array.  
  
 Jeśli zmienna przechowuje wskaźnik do wystąpienia klasy, która nie jest znana w czasie kompilacji, lub jeśli może wskazywać dane różnych typów danych, należy zadeklarować ją jako `Object`.  
  
 Zaletą typu danych `Object` jest możliwość użycia go do przechowywania danych dowolnego typu danych. Wadą jest to, że ponosisz dodatkowe operacje, które wykonują więcej czasu wykonywania, i zwiększają działanie aplikacji. Jeśli używasz zmiennej `Object` dla typów wartości, naliczane są *opakowanie* i *rozpakowywanie*. Jeśli używasz jej do typów referencyjnych, naliczane są *późne powiązania*.  
  
## <a name="see-also"></a>Zobacz także

- [Znaki typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Typy danych podstawowych](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Typy danych liczbowych](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Znakowe typy danych](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Wczesne i późne powiązania](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
