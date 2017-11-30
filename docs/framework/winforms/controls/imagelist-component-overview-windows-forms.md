---
title: "ImageList — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ImageList
helpviewer_keywords:
- collection controls [Windows Forms], images
- icon list control
- ImageList component [Windows Forms], about ImageList component
ms.assetid: 7e25d89b-5633-40c1-afc3-82e0e301ffa2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 02fb14b84341d594f35885be220027631999d202
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imagelist-component-overview-windows-forms"></a>ImageList — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.ImageList> składnik jest używany do przechowywania obrazów, które mogą być następnie wyświetlane przez formanty. Listy obrazów umożliwia pisanie kodu dla wykazu powinny być zawsze obrazów. Na przykład można obracać obrazów wyświetlanych przez <xref:System.Windows.Forms.Button> formantu, zmieniając po prostu przycisku <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> lub <xref:System.Windows.Forms.ButtonBase.ImageKey%2A> właściwości. Można również kojarzyć tej samej listy obrazów z wielu formantów. Na przykład, jeśli używasz zarówno <xref:System.Windows.Forms.ListView> kontroli i <xref:System.Windows.Forms.TreeView> formantu, aby wyświetlić tę samą listę plików, zmieniając ikonę pliku na liście obrazów spowoduje, że nowa ikona pojawią się w obu widokach.  
  
## <a name="using-imagelist-with-controls"></a>Przy użyciu listy obrazów z formantami  
 Można użyć listy obrazów z żadnego formantu, który ma `ImageList` właściwości — lub w przypadku liczby <xref:System.Windows.Forms.ListView> kontroli, <xref:System.Windows.Forms.ListView.SmallImageList%2A> i <xref:System.Windows.Forms.ListView.LargeImageList%2A> właściwości. Formanty, które mogą być skojarzone z listy obrazów obejmują: <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.ToolBar>, <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.CheckBox>, <xref:System.Windows.Forms.RadioButton>, i <xref:System.Windows.Forms.Label> kontrolki. Aby skojarzyć listy obrazów z formantem, ustaw dla formantu `ImageList` właściwość na nazwę <xref:System.Windows.Forms.ImageList> składnika.  
  
## <a name="key-properties"></a>Właściwości klucza  
 Właściwość klucza <xref:System.Windows.Forms.ImageList> składnik jest <xref:System.Windows.Forms.ImageList.Images%2A>, zawierający obrazy, które mają być używane przez skojarzony formant. Każdy poszczególnych obraz jest dostępny przez jej wartość indeksu lub za pomocą klucza. <xref:System.Windows.Forms.ImageList.ColorDepth%2A> Właściwość określa liczbę kolorów, które mają być renderowane obrazów z. Obrazy wszystkie pojawi się w tym samym rozmiarze, ustawione przez <xref:System.Windows.Forms.ImageList.ImageSize%2A> właściwości. Obrazy, które są większe będą skalowane w celu dopasowania.  
  
 Jeśli używasz [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], masz dostęp do dużych biblioteki standardowe obrazów, które można używać w aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ImageList>  
 [Porady: Dodawanie lub usuwanie obrazów za pomocą systemu Windows składnika ImageList formularzy](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
