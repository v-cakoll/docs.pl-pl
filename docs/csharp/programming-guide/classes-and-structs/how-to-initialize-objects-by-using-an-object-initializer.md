---
title: 'Porady: inicjowanie obiektów za pomocą inicjatora obiektów (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 1f5f068cd8dc3787eb8cb2cd72cc30e9ea159390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>Porady: inicjowanie obiektów za pomocą inicjatora obiektów (Przewodnik programowania w języku C#)
Inicjatory obiektów służy do zainicjowania obiekty typu w sposób deklaratywne bez jawnego wywołania konstruktora dla typu.  
  
 Poniższe przykłady przedstawiają sposób inicjatory obiektów za pomocą nazwane obiekty. Procesy kompilatora obiekt inicjatory pierwszy uzyskiwanie dostępu do domyślnego konstruktora wystąpienia, a następnie przetwarzania operacji inicjowania elementu członkowskiego. W związku z tym jeśli domyślny konstruktor jest zadeklarowany jako `private` w klasie, inicjatory obiektów, które wymagają dostępu publicznego zakończy się niepowodzeniem.  
  
 Jeśli definiujesz typu anonimowego, należy użyć inicjatora obiektu. Aby uzyskać więcej informacji, zobacz [porady: zwraca podzestawy elementu właściwości w zapytaniu](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zainicjować nowe `StudentName` typu przy użyciu inicjatory obiektów.  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zainicjować to zbiór `StudentName` typów za pomocą inicjatora kolekcji. Należy pamiętać, że inicjatora kolekcji serii inicjatory obiektów rozdzielonych przecinkami.  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Aby uruchomić ten kod, skopiuj i Wklej klasy w projektach Visual C# console aplikacji utworzony w programie Visual Studio.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
