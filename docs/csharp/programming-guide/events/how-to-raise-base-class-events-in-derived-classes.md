---
title: Jak podnieść zdarzenia klasy podstawowej w klasach pochodnych — Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 48f95871aa8a5a33923286262093a143cbd16d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712328"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Jak podnieść zdarzenia klasy podstawowej w klasach pochodnych (Przewodnik programowania C#)
Poniższy prosty przykład pokazuje standardowy sposób deklarowania zdarzeń w klasie podstawowej, dzięki czemu mogą być również wywoływane z klas pochodnych. Ten wzorzec jest szeroko stosowany w klasach formularzy systemu Windows w bibliotece klas .NET Framework.  
  
 Podczas tworzenia klasy, która może służyć jako klasa podstawowa dla innych klas, należy wziąć pod uwagę fakt, że zdarzenia są specjalnym typem delegata, który może być wywoływany tylko z wewnątrz klasy, która je zadeklarowała. Klasy pochodne nie można bezpośrednio wywołać zdarzenia, które są zadeklarowane w klasie podstawowej. Chociaż czasami może chcesz zdarzenie, które mogą być wywoływane tylko przez klasę podstawową, w większości czasu, należy włączyć klasy pochodnej do wywoływania zdarzeń klasy podstawowej. Aby to zrobić, można utworzyć metodę wywoływania chronione w klasie podstawowej, która otacza zdarzenie. Wywołując lub zastępując tę metodę wywoływania, klasy pochodne można wywołać zdarzenie pośrednio.  
  
> [!NOTE]
> Nie deklaruj zdarzeń wirtualnych w klasie podstawowej i nie należy je zastępować w klasie pochodnej. Kompilator Języka C# nie obsługuje tych poprawnie i jest nieprzewidywalne, czy subskrybent akcesorii do zdarzenia pochodnego będzie faktycznie subskrybowania zdarzenia klasy podstawowej.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideEvents#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Zdarzenia](./index.md)
- [Delegaty](../delegates/index.md)
- [Modyfikatory dostępu](../classes-and-structs/access-modifiers.md)
- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
