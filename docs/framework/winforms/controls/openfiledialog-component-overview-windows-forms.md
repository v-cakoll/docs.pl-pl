---
title: "OpenFileDialog — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3e5dc6630d9bc7a2090a28daabbf08eeed59005
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.OpenFileDialog> składnik jest okno dialogowe wstępnie skonfigurowane. Jest to ten sam **Otwórz plik** okno dialogowe udostępnianych przez system operacyjny Windows. Dziedziczy on z <xref:System.Windows.Forms.CommonDialog> klasy.  
  
## <a name="using-this-component"></a>Przy użyciu tego składnika  
 Użyj tego składnika w aplikacji opartych na systemie Windows jako prostym rozwiązaniem dla wyboru plików zamiast własne okno dialogowe Konfigurowanie. Polegając na standardowe okno dialogowe systemu Windows, możesz utworzyć aplikacje, których podstawowych funkcji jest znane użytkowników. Należy jednak pamiętać, że w przypadku przy użyciu <xref:System.Windows.Forms.OpenFileDialog> składnika, należy napisać logiki otwierania pliku.  
  
 Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę w celu wyświetlenia okna dialogowego w czasie wykonywania. Można umożliwić użytkownikom wybrać wiele plików do otwarcia z <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> właściwości. Ponadto można użyć <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> właściwości w celu określenia, czy pola wyboru tylko do odczytu jest wyświetlany w oknie dialogowym. <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Właściwość wskazuje, czy zaznaczone jest pole wyboru tylko do odczytu. Na koniec <xref:System.Windows.Forms.FileDialog.Filter%2A> właściwość ustawia bieżącego pliku nazwę ciąg filtru, który określa opcje, które są wyświetlane w polu "Pliki typu" w oknie dialogowym.  
  
 Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.OpenFileDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog, składnik](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
