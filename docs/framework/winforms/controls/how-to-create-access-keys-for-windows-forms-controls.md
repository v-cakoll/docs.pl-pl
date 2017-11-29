---
title: "Porady: tworzenie klawiszy dostępu dla formantów formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: af4cbcc5dacc4f9a0b5312b67838479bf6817228
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Porady: tworzenie klawiszy dostępu dla formantów formularzy systemu Windows
*Klucz dostępu* jest podkreślony znak w tekście menu, element menu lub etykiety formantu, takie jak przycisk. Przy użyciu klucza dostępu użytkownika może "przycisk" naciśnięcie klawisza ALT w połączeniu z kluczem dostępu wstępnie zdefiniowane. Na przykład, gdy przycisk działa procedura Drukowanie formularza i dlatego jego `Text` właściwość jest ustawiona na "Print","Dodawanie handlowego" i "przed litery"P"powoduje, że litery"P", aby podkreślić tekst przycisku w czasie wykonywania. Użytkownik może uruchomić polecenie skojarzone z przyciskiem, naciskając klawisze ALT + P. Nie może mieć klucza dostępu dla formantu, który nie może uzyskać fokusu.  
  
### <a name="to-create-an-access-key-for-a-control"></a>Aby utworzyć klucz dostępu dla formantu  
  
1.  Ustaw `Text` właściwości ciąg, który zawiera handlowego "i" (&) przed literą, która będzie skrótu.  
  
    ```vb  
    ' Set the letter "P" as an access key.  
    Button1.Text = "&Print"  
    ```  
  
    ```csharp  
    // Set the letter "P" as an access key.  
    button1.Text = "&Print";  
    ```  
  
    ```cpp  
    // Set the letter "P" as an access key.  
    button1->Text = "&Print";  
    ```  
  
    > [!NOTE]
    >  Aby uwzględnić znak podpis bez tworzenia klucza dostępu, obejmują dwa ampersandu (& &). Pojedynczy znak jest wyświetlana w podpisie i żadne znaki nie są podkreślone.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Button>  
 [Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Porady: Ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Etykietowanie formantów formularzy systemu Windows poszczególnych i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
