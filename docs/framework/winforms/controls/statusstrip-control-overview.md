---
title: StatusStrip — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
ms.openlocfilehash: f6f2d4b19b7ec91c964c72e3aca85e0253c7cc22
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009646"
---
# <a name="statusstrip-control-overview"></a>StatusStrip — Informacje o formancie
A <xref:System.Windows.Forms.StatusStrip> kontrolka Wyświetla informacje dotyczące obiektu są wyświetlane na <xref:System.Windows.Forms.Form>, składniki obiektu lub informacji kontekstowych, które odnoszą się do tego obiektu operacji w ramach aplikacji. Zazwyczaj <xref:System.Windows.Forms.StatusStrip> kontrola składa się z <xref:System.Windows.Forms.ToolStripStatusLabel> obiektów, z których każda wyświetla tekst i/lub ikonę. <xref:System.Windows.Forms.StatusStrip> Może również zawierać <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, i <xref:System.Windows.Forms.ToolStripProgressBar> kontrolki.  
  
 Wartość domyślna <xref:System.Windows.Forms.StatusStrip> ma nie paneli. Aby dodać zespoły do <xref:System.Windows.Forms.StatusStrip>, użyj <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> metody.  
  
 Brak rozbudowana Obsługa obsługi <xref:System.Windows.Forms.StatusStrip> elementów i Typowe polecenia w programie Visual Studio.  
  
 Zobacz też [StatusStrip — Edytor kolekcji elementów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233631(v=vs.100)) i [StatusStrip — okno dialogowe zadania](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233642(v=vs.100)).  
  
 Mimo że <xref:System.Windows.Forms.StatusStrip> zastępuje i rozszerza <xref:System.Windows.Forms.StatusBar> kontrolki z poprzednich wersji <xref:System.Windows.Forms.StatusBar> został zachowany na potrzeby zgodności z poprzednimi wersjami i użycia w przyszłości wybranie opcji.  
  
### <a name="important-statusstrip-members"></a>StatusStrip — ważne elementy członkowskie  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.StatusStrip> obsługuje przepełnienie funkcji.|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.StatusStrip> odcinkach od końca do końca w jego <xref:System.Windows.Forms.ToolStripContainer>.|  
  
### <a name="important-statusstrip-companion-classes"></a>Klasy ważne pomocnika StatusStrip  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Reprezentuje panelu w <xref:System.Windows.Forms.StatusStrip> kontroli.|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Wyświetla skojarzoną <xref:System.Windows.Forms.ToolStripDropDown> z którego użytkownik może wybrać jeden element.|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Reprezentuje kontrolkę legalną dwuczęściową przycisk standardowy i menu rozwijanego.|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Wyświetla stan ukończenia procesu.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
