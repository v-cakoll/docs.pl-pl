---
title: 'Instrukcje: Wywoływanie zdarzeń klasy podstawowej w klasach pochodnych - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
ms.openlocfilehash: 6d6e84861ec48be5bccbc050624b0843947cb727
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539867"
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Instrukcje: Wywoływanie zdarzeń klasy podstawowej w klasach pochodnych (C# Programming Guide)
Poniższym prostym przykładzie pokazano standardowy sposób, aby zadeklarować zdarzenia w klasie bazowej, dzięki czemu mogą one również inicjowane z klas pochodnych. Ten wzorzec jest często używane klasy formularzy Windows w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas.  
  
 Kiedy tworzysz klasę, która może służyć jako klasa bazowa innych klas, należy rozważyć fakt, że zdarzenia są specjalnym typem delegata, który można wywołać tylko z w obrębie klasy, która je zadeklarować. Klasy pochodne nie można bezpośrednio wywołać zdarzenia, które są zadeklarowane w klasie bazowej. Chociaż czasami możesz chcieć zdarzenie, które tylko będzie zgłaszany przez klasę bazową, w większości przypadków, należy włączyć klasy pochodnej w celu wywoływanie zdarzeń klasy podstawowej. Aby to zrobić, można utworzyć chronionych wywołania metody w klasie bazowej, która otacza zdarzenia. Przez wywołanie lub zastąpienie tego wywołania metody, klasy pochodne mogą być wywoływane zdarzenie pośrednio.  
  
> [!NOTE]
>  Deklarowanie zdarzeń wirtualnych w klasie bazowej i nie je zastąpić w klasie pochodnej. Kompilator języka C# nie obsługują one poprawnie i jest nieprzewidywalne czy subskrybent zdarzenia pochodnej faktycznie będzie subskrybowanie zdarzeń klasy podstawowej.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)
- [Delegaty](../../../csharp/programming-guide/delegates/index.md)
- [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
