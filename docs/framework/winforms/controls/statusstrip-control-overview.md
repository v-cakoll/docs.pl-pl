---
title: "StatusStrip — Informacje o formancie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: StatusStrip
helpviewer_keywords:
- StatusStrip control [Windows Forms], about StatusStrip control
- status bars [Windows Forms], about status bars
ms.assetid: c0d9bcbb-f8b8-46ef-bae2-4146b8c8ce99
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6d1eb698dbb9168bf5de6d3982e19e69d170ac0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="statusstrip-control-overview"></a>StatusStrip — Informacje o formancie
A <xref:System.Windows.Forms.StatusStrip> kontroli Wyświetla informacje o przeglądanym na obiekt <xref:System.Windows.Forms.Form>, składniki obiektu lub informacje kontekstowe, które odnoszą się do tego obiektu operacji w aplikacji. Zazwyczaj <xref:System.Windows.Forms.StatusStrip> kontrola składa się z <xref:System.Windows.Forms.ToolStripStatusLabel> obiektów, z których każdy zawiera tekst i ikony. <xref:System.Windows.Forms.StatusStrip> Może również zawierać <xref:System.Windows.Forms.ToolStripDropDownButton>, <xref:System.Windows.Forms.ToolStripSplitButton>, i <xref:System.Windows.Forms.ToolStripProgressBar> kontrolki.  
  
 Wartość domyślna <xref:System.Windows.Forms.StatusStrip> ma nie paneli. Aby dodać paneli <xref:System.Windows.Forms.StatusStrip>, użyj <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A?displayProperty=nameWithType> metody.  
  
 Brak kompleksową obsługę Obsługa <xref:System.Windows.Forms.StatusStrip> elementów i Typowe polecenia programu Visual Studio.  
  
 Zobacz też [edytora kolekcji elementy StatusStrip](http://msdn.microsoft.com/library/ms233631\(v=vs.110\)), [okno dialogowe zadania StatusStrip](http://msdn.microsoft.com/library/ms233642\(v=vs.110\)).  
  
 Mimo że <xref:System.Windows.Forms.StatusStrip> zastępuje i rozszerza <xref:System.Windows.Forms.StatusBar> kontrolę nad poprzednie wersje <xref:System.Windows.Forms.StatusBar> są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.  
  
### <a name="important-statusstrip-members"></a>Elementy członkowskie ważne StatusStrip  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.StatusStrip.CanOverflow%2A>|Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.StatusStrip> obsługuje przepełnienie funkcji.|  
|<xref:System.Windows.Forms.StatusStrip.Stretch%2A>|Pobiera lub ustawia wartość wskazującą czy <xref:System.Windows.Forms.StatusStrip> odcinkach od końca do końca w jego <xref:System.Windows.Forms.ToolStripContainer>.|  
  
### <a name="important-statusstrip-companion-classes"></a>Klasy ważnym dodatkiem StatusStrip  
  
|Nazwa|Opis|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Reprezentuje panelu w <xref:System.Windows.Forms.StatusStrip> formantu.|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Wyświetla skojarzony <xref:System.Windows.Forms.ToolStripDropDown> z którego użytkownik może wybrać jeden element.|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|Reprezentuje kontrolkę dwóch części, która jest przycisk standardowy i menu rozwijanego.|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|Wyświetla stan ukończenia procesu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>
