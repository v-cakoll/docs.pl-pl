---
title: Jak wywoływać zdarzenia klasy podstawowej w klasach pochodnych C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 48f95871aa8a5a33923286262093a143cbd16d40
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712328"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Jak wywoływać zdarzenia klasy podstawowej w klasach pochodnychC# (Przewodnik programowania)
Poniższy prosty przykład pokazuje standardowy sposób deklarowania zdarzeń w klasie bazowej, aby mogły być również wywoływane z klas pochodnych. Ten wzorzec jest szeroko używany w klasach Windows Forms w bibliotece klas .NET Framework.  
  
 Podczas tworzenia klasy, która może być używana jako klasa bazowa dla innych klas, należy wziąć pod uwagę fakt, że zdarzenia są specjalnym typem delegata, który może być wywoływany tylko z klasy, która je zadeklaruje. Klasy pochodne nie mogą bezpośrednio wywoływać zdarzeń, które są zadeklarowane w klasie bazowej. Chociaż czasami można chcieć, aby zdarzenie, które może zostać wywołane tylko przez klasę bazową, w większości przypadków należy włączyć klasę pochodną, aby wywoływać zdarzenia klasy bazowej. W tym celu można utworzyć chronioną metodę wywołującą w klasie bazowej, która otacza zdarzenie. Wywołując lub zastępując tę metodę wywołującą, klasy pochodne mogą wywołać zdarzenie pośrednio.  
  
> [!NOTE]
> Nie deklaruj zdarzeń wirtualnych w klasie podstawowej i zastąp je w klasie pochodnej. C# Kompilator nie obsługuje tych poprawnie i jest nieprzewidywalne, niezależnie od tego, czy subskrybent zdarzenia pochodnego rzeczywiście zasubskrybuje zdarzenie klasy bazowej.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zdarzenia](./index.md)
- [Delegaci](../delegates/index.md)
- [Modyfikatory dostępu](../classes-and-structs/access-modifiers.md)
- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
