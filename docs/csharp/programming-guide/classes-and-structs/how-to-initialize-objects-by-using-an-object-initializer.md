---
title: 'Porady: inicjowanie obiektów za pomocą inicjatora obiektów (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 0b103513bdcdef42c61172d1cc0ee096264a9559
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521558"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Porady: inicjowanie obiektów za pomocą inicjatora obiektów (Przewodnik programowania w języku C#)
Inicjatory obiektów można użyć do zainicjowania obiekty typu w sposób deklaratywne, bez jawnego wywołania konstruktora dla typu.  
  
 Poniższe przykłady pokazują, jak używać inicjatory obiektów z nazwane obiekty. Procesy kompilatora obiekt inicjatory pierwszego uzyskiwania dostępu do domyślnego konstruktora wystąpienia, a następnie przetwarzania operacji inicjowania elementu członkowskiego. W związku z tym jeśli domyślny konstruktor jest zadeklarowany jako `private` w klasie inicjatorów obiektów, które wymagają dostępu publicznego zakończy się niepowodzeniem.  
  
 Jeśli definiujesz typ anonimowy, należy użyć inicjatora obiektu. Aby uzyskać więcej informacji, zobacz [jak: zwraca podzestawy elementu właściwości w zapytaniu](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zainicjować nowy `StudentName` typu przy użyciu inicjatorów obiektów.  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zainicjować kolekcję `StudentName` typów za pomocą inicjatora kolekcji. Należy pamiętać, że inicjator kolekcji serii inicjatorów obiektów rozdzielonych przecinkami.  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i Wklej klasy Visual C# projekt aplikacji konsoli, która została utworzona w programie Visual Studio.  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
