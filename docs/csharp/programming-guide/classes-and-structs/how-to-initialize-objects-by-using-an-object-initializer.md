---
title: "Porady: inicjowanie obiektów za pomocą inicjatora obiektów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d1e65f8519062f6bceeb466a3b72c5719c0918f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 Aby uruchomić ten kod, skopiuj i Wklej klasy w projektach Visual C# console aplikacji utworzony w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
