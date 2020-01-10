---
title: Przykładowa Klasa COM C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6af85d0314a44acbde0996cecbe6dad82cdcc8db
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712081"
---
# <a name="example-com-class-c-programming-guide"></a>Klasa COM — Przykład (Przewodnik programowania w języku C#)
Poniżej znajduje się przykład klasy, którą można uwidocznić jako obiekt COM. Gdy ten kod został umieszczony w pliku CS i dodany do projektu, ustaw właściwość **Register for com Interop** na **wartość true**. Aby uzyskać więcej informacji, zobacz [How to: register a Component for com Interop](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).
  
 Uwidacznianie C# obiektów wizualnych do modelu COM wymaga zadeklarowania interfejsu klasy, interfejsu zdarzeń, jeśli jest to wymagane, i samej klasy. Elementy członkowskie klasy muszą być zgodne z tymi regułami, aby były widoczne dla modelu COM:  
  
- Klasa musi być publiczna.  
  
- Właściwości, metody i zdarzenia muszą być publiczne.  
  
- Właściwości i metody muszą być zadeklarowane w interfejsie klasy.  
  
- Zdarzenia muszą być zadeklarowane w interfejsie zdarzenia.  
  
 Inne publiczne elementy członkowskie klasy, które nie są zadeklarowane w tych interfejsach, nie będą widoczne dla modelu COM, ale będą widoczne dla innych obiektów .NET Framework.  
  
 Aby uwidocznić właściwości i metody dla modelu COM, należy je zadeklarować w interfejsie klasy i oznaczyć je atrybutem `DispId` i zaimplementować w klasie. Kolejność, w której elementy członkowskie są zadeklarowane w interfejsie, jest kolejnością używaną w przypadku tablic wirtualnych COM.  
  
 Aby uwidocznić zdarzenia z klasy, należy je zadeklarować w interfejsie zdarzeń i oznaczyć je atrybutem `DispId`. Klasa nie powinna implementować tego interfejsu.  
  
 Klasa implementuje interfejs klasy; może zaimplementować więcej niż jeden interfejs, ale Pierwsza implementacja będzie domyślnym interfejsem klasy. W tym miejscu Zaimplementuj metody i właściwości uwidocznione w modelu COM. Muszą być oznaczone jako publiczne i muszą być zgodne z deklaracjami w interfejsie klasy. Ponadto w tym miejscu Zadeklaruj zdarzenia zgłoszone przez klasę. Muszą być oznaczone jako publiczne i muszą być zgodne z deklaracjami w interfejsie zdarzeń.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Współdziałanie](./index.md)
- [Strona kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
