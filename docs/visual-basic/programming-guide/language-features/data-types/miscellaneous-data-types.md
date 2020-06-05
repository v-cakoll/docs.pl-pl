---
title: Różne typy danych
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: 0a08c0e7087c3efb0e5ffce51182defae45629ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393756"
---
# <a name="miscellaneous-data-types-visual-basic"></a>Różne typy danych (Visual Basic)
Visual Basic dostarcza kilka typów danych, które nie są zorientowane na numery lub znaki. Zamiast tego zajmują się one wyspecjalizowanymi danymi, takimi jak tak/nie wartości, wartości daty/godziny i adresy obiektów.  
  
 Aby uzyskać tabelę zawierającą porównanie równoległe typów danych Visual Basic, zobacz [typy danych](../../../language-reference/data-types/index.md).  
  
## <a name="boolean-type"></a>Typ wartości logicznej  
 [Typ danych Boolean](../../../language-reference/data-types/boolean-data-type.md) jest wartością bez znaku, która jest interpretowana jako `True` lub `False` . Szerokość danych zależy od platformy implementującej. Jeśli zmienna może zawierać tylko wartości dwustanowe, takie jak true/false, yes/no lub on/off, deklaruj ją jako `Boolean` .  
  
## <a name="date-type"></a>Typ daty  
 [Typ danych Data](../../../language-reference/data-types/date-data-type.md) jest wartością 64-bitową, która zawiera informacje o dacie i godzinie. Każdy przyrost reprezentuje 100 nanosekund czasu, od momentu rozpoczęcia (12:00 AM) 1 stycznia roku 1 w kalendarzu gregoriańskim. Jeśli zmienna może zawierać wartość typu Date, wartość czasu lub obie te metody, deklaruj ją jako `Date` .  
  
## <a name="object-type"></a>Typ obiektu  
 [Typ danych obiektu](../../../language-reference/data-types/object-data-type.md) jest adresem 32-bitowym, który wskazuje na wystąpienie obiektu w aplikacji lub w innej aplikacji. `Object`Zmienna może odwoływać się do dowolnego obiektu rozpoznawanego przez aplikację lub do danych dowolnego typu danych. Obejmuje to zarówno *typy wartości*, jak `Integer` `Boolean` i wystąpienia struktury oraz *typy odwołań*, które są wystąpieniami obiektów utworzonych na podstawie klas takich jak `String` i i <xref:System.Windows.Forms.Form> .  
  
 Jeśli zmienna przechowuje wskaźnik do wystąpienia klasy, która nie jest znana w czasie kompilacji, lub jeśli może wskazywać dane różnych typów danych, należy zadeklarować je jako `Object` .  
  
 Zaletą tego `Object` typu danych jest możliwość użycia go do przechowywania danych dowolnego typu danych. Wadą jest to, że ponosisz dodatkowe operacje, które wykonują więcej czasu wykonywania, i zwiększają działanie aplikacji. Jeśli używasz `Object` zmiennej dla typów wartości, naliczane jest *opakowanie* i *rozpakowywanie*. Jeśli używasz jej do typów referencyjnych, naliczane są *późne powiązania*.  
  
## <a name="see-also"></a>Zobacz też

- [Znaki typu](type-characters.md)
- [Typy danych podstawowych](elementary-data-types.md)
- [Typy danych liczbowych](numeric-data-types.md)
- [Znakowe typy danych](character-data-types.md)
- [Rozwiązywanie problemów związanych z typami danych](troubleshooting-data-types.md)
- [Wczesne i późne powiązania](../early-late-binding/index.md)
