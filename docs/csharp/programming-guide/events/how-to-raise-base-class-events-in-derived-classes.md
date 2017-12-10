---
title: "Porady: wywoływanie zdarzeń klasy podstawowej w klasach pochodnych (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c9da65958ce827fab642f4a6310d0c68dfb951a6
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Porady: wywoływanie zdarzeń klasy podstawowej w klasach pochodnych (Przewodnik programowania w języku C#)
W poniższym przykładzie prosty przedstawiono standardowy sposób, aby zadeklarować zdarzenia w klasie podstawowej, dzięki czemu również może być wywoływane z klasy pochodnej. Ten wzorzec jest bardzo często używane w klasach formularzy systemu Windows w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas.  
  
 Podczas tworzenia klasy, która może służyć jako klasę podstawową innych klas należy rozważyć fakt, że zdarzenia są specjalny typ delegata, który można wywołać tylko z należące do klasy zadeklarowany je. Klasy pochodne nie mogą wywoływać bezpośrednio zdarzenia, które są zadeklarowane w klasie podstawowej. Jednak czasami może być zdarzenie, które może być zgłaszany tylko przez klasy podstawowej, w większości przypadków, należy włączyć klasy pochodnej w celu wywoływać zdarzeń klasy podstawowej. Aby to zrobić, można utworzyć chronionego wywoływanie metody w klasie podstawowej, która opakowuje zdarzenia. Przez wywołanie lub zastąpienie tego wywoływanie metody, klasy pochodne mogą wywoływać zdarzenia pośrednio.  
  
> [!NOTE]
>  Nie deklaruje wirtualnego zdarzenia w klasie podstawowej i zastąpić je w klasie pochodnej. Kompilator języka C# nie obsługuje te poprawnie i jest nieprzewidywalne czy subskrybentom pochodnej zdarzeń faktycznie będzie subskrybowanie zdarzeń klasy podstawowej.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
 [Obiekty delegowane](../../../csharp/programming-guide/delegates/index.md)  
 [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Tworzenie programów obsługi zdarzeń w formularzach systemu Windows](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
