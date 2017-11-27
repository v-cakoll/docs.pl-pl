---
title: "Klasa COM — Przykład (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad14b414c037d38da55ce0ec82685b790cc46d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="example-com-class-c-programming-guide"></a>Klasa COM — Przykład (Przewodnik programowania w języku C#)
Oto przykład klasy, która może narazić jako obiekt COM. Po ten kod został umieszczony w pliku .cs i dodane do projektu, ustawić **Zarejestruj dla międzyoperacyjności z modelem COM** właściwości **True**. Aby uzyskać więcej informacji, zobacz [NIB: jak: zarejestrować składnika COM Interop](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e).  
  
 Udostępnianie obiektów Visual C# dla modelu COM wymaga deklarowanie interfejsu klasy, interfejsu zdarzenia w razie potrzeby i samej klasy. Elementy członkowskie klasy, wykonaj te reguły mają być widoczne dla modelu COM:  
  
-   Klasy muszą być publiczne.  
  
-   Właściwości, metod i zdarzeń muszą być publiczne.  
  
-   Właściwości i metody, musi zostać zadeklarowany w interfejsie klasa.  
  
-   Zdarzenia musi zostać zadeklarowany w zdarzeniu interfejsu.  
  
 Inne publiczne elementy członkowskie w klasie, które nie są zadeklarowane w tych interfejsów nie będą widoczne dla modelu COM, ale będą one widoczne dla innych obiektów .NET Framework.  
  
 Do udostępnienia właściwości i metody dla modelu COM, należy zadeklarować je w interfejsie klasa i oznacz je za pomocą `DispId` atrybutu i ich wdrażania w klasie. Kolejność, w jakiej elementy członkowskie są zadeklarowane w interfejsie jest kolejność używaną dla COM vtable.  
  
 Do udostępnienia zdarzenia z klasy, należy zadeklarować je dla interfejsu zdarzenia i oznacz je za pomocą `DispId` atrybutu. Klasa nie powinny implementować ten interfejs.  
  
 Klasa implementuje interfejs klasy; można zaimplementować więcej niż jeden interfejs, ale implementacja pierwszy będzie domyślnego interfejsu klasy. Implementuje metody i właściwości ujawniony dla modelu COM w tym miejscu. One musi być oznaczona jako publiczna i musi być zgodna z deklaracjami w interfejsie klasa. Ponadto należy zadeklarować zdarzenia wygenerowane przez klasę w tym miejscu. One musi być oznaczona jako publiczna i musi być zgodna z deklaracji zdarzenia interfejsu.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Współdziałanie](../../../csharp/programming-guide/interop/index.md)  
 [Strona kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
