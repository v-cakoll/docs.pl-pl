---
title: Użycie podwójnego buforowania
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 5b22336221c7bdda3c9dd7adf23308a2b0bad450
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169918"
---
# <a name="using-double-buffering"></a>Użycie podwójnego buforowania
Podwójnie buforowana grafika umożliwia zmniejszanie migotania w swoich aplikacjach, które zawierają działania złożonego rysowania. .NET Framework zawiera wbudowaną obsługę podwójnego buforowania, lub możesz zarządzać i ręczne Renderowanie grafiki.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podwójnie buforowana grafika](double-buffered-graphics.md)  
 Wprowadzenie obsługi podwójnego buforowania pojęcia i przedstawiono .NET Framework.  
  
 [Instrukcje: Zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 Pokazuje, jak użyć domyślnego podwójnego buforowania pomocy technicznej w programie .NET Framework.  
  
 [Instrukcje: Ręczne zarządzanie buforowaną grafiką](how-to-manually-manage-buffered-graphics.md)  
 Pokazuje, jak zarządzać podwójnego buforowania w aplikacjach.  
  
 [Instrukcje: Ręczne renderowanie buforowanej grafiki](how-to-manually-render-buffered-graphics.md)  
 Pokazuje sposób renderowania podwójnie buforowana grafika.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Control.SetStyle%2A> Metoda kontrolki, która umożliwia podwójnego buforowania.  
  
 <xref:System.Drawing.BufferedGraphicsContext> Udostępnia metody do tworzenia bufory grafiki typu.  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 Zapewnia dostęp do kontekstu buforowaną grafiką dla domeny aplikacji.
