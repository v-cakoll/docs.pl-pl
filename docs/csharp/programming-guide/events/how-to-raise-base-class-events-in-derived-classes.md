---
title: Jak wywoływać zdarzenia klasy podstawowej w klasach pochodnych — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: e2d2dfc2809a4de1756bfc362880eebc79076b94
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240632"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Jak wywoływać zdarzenia klasy podstawowej w klasach pochodnych (Przewodnik programowania w języku C#)
Poniższy prosty przykład pokazuje standardowy sposób deklarowania zdarzeń w klasie bazowej, aby mogły być również wywoływane z klas pochodnych. Ten wzorzec jest szeroko używany w Windows Forms klasach w bibliotekach klas .NET.  
  
 Podczas tworzenia klasy, która może być używana jako klasa bazowa dla innych klas, należy wziąć pod uwagę fakt, że zdarzenia są specjalnym typem delegata, który może być wywoływany tylko z klasy, która je zadeklaruje. Klasy pochodne nie mogą bezpośrednio wywoływać zdarzeń, które są zadeklarowane w klasie bazowej. Chociaż czasami można chcieć, aby zdarzenie, które może zostać wywołane tylko przez klasę bazową, w większości przypadków należy włączyć klasę pochodną, aby wywoływać zdarzenia klasy bazowej. W tym celu można utworzyć chronioną metodę wywołującą w klasie bazowej, która otacza zdarzenie. Wywołując lub zastępując tę metodę wywołującą, klasy pochodne mogą wywołać zdarzenie pośrednio.  
  
> [!NOTE]
> Nie deklaruj zdarzeń wirtualnych w klasie podstawowej i zastąp je w klasie pochodnej. Kompilator języka C# nie obsługuje tych poprawnie i jest nieprzewidywalne, czy subskrybent zdarzenia pochodnego rzeczywiście zasubskrybuje zdarzenie klasy bazowej.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Zdarzenia](./index.md)
- [Delegaci](../delegates/index.md)
- [Modyfikatory dostępu](../classes-and-structs/access-modifiers.md)
- [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
