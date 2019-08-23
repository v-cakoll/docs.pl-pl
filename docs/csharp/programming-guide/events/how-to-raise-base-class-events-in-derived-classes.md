---
title: 'Instrukcje: Wywoływanie zdarzeń klasy podstawowej w klasach C# pochodnych — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 820bdcb895a1c3eb7c56db55b298c1a9636f2f85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921876"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Instrukcje: Wywołaj zdarzenia klasy podstawowej w klasachC# pochodnych (Przewodnik programowania)
Poniższy prosty przykład pokazuje standardowy sposób deklarowania zdarzeń w klasie bazowej, aby mogły być również wywoływane z klas pochodnych. Ten wzorzec jest szeroko używany w klasach Windows Forms w bibliotece klas .NET Framework.  
  
 Podczas tworzenia klasy, która może być używana jako klasa bazowa dla innych klas, należy wziąć pod uwagę fakt, że zdarzenia są specjalnym typem delegata, który może być wywoływany tylko z klasy, która je zadeklaruje. Klasy pochodne nie mogą bezpośrednio wywoływać zdarzeń, które są zadeklarowane w klasie bazowej. Chociaż czasami można chcieć, aby zdarzenie, które może zostać wywołane tylko przez klasę bazową, w większości przypadków należy włączyć klasę pochodną, aby wywoływać zdarzenia klasy bazowej. W tym celu można utworzyć chronioną metodę wywołującą w klasie bazowej, która otacza zdarzenie. Wywołując lub zastępując tę metodę wywołującą, klasy pochodne mogą wywołać zdarzenie pośrednio.  
  
> [!NOTE]
> Nie deklaruj zdarzeń wirtualnych w klasie podstawowej i zastąp je w klasie pochodnej. C# Kompilator nie obsługuje tych poprawnie i jest nieprzewidywalne, niezależnie od tego, czy subskrybent zdarzenia pochodnego rzeczywiście zasubskrybuje zdarzenie klasy bazowej.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Zdarzenia](./index.md)
- [Delegaty](../delegates/index.md)
- [Modyfikatory dostępu](../classes-and-structs/access-modifiers.md)
- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
