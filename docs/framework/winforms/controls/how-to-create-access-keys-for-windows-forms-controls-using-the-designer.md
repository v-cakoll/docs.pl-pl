---
title: "Porady: tworzenie klawiszy dostępu dla formantów formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 19c47c21526ca6e7aa4046a1853f3d1743438d17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Porady: tworzenie klawiszy dostępu dla formantów formularzy systemu Windows przy użyciu narzędzia Projektant
*Klucz dostępu* jest podkreślony znak w tekście menu, element menu lub etykiety formantu, takie jak przycisk. Umożliwia użytkownikowi "przycisk" naciśnięcie klawisza ALT w połączeniu z kluczem dostępu wstępnie zdefiniowane. Na przykład, gdy przycisk działa procedura Drukowanie formularza i dlatego jego `Text` właściwość ma wartość "Print" Dodawanie ampersand (&) przed literą "P" powoduje, że litery "P", aby podkreślić tekst przycisku w czasie wykonywania. Użytkownik może uruchomić polecenie skojarzone z przyciskiem, naciskając klawisze ALT + P. Nie może mieć klucza dostępu dla formantu, który nie może uzyskać fokusu.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-access-key-for-a-control"></a>Aby utworzyć klucz dostępu dla formantu  
  
1.  W **właściwości** ustaw `Text` właściwości ciąg, który zawiera handlowego "i" (&) przed literą, która będzie klucz dostępu. Na przykład aby ustawić literę "P" jako klawisz dostępu, wpisz **& Drukuj** w siatce.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Button>  
 [Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Porady: Ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Etykietowanie formantów formularzy systemu Windows poszczególnych i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
