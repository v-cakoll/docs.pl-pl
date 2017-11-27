---
title: 'Porady: dodawanie kontrolek ActiveX do formularzy systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: afee07f2f5009abb6cf8facc94b138f4ea2a11fd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Porady: dodawanie kontrolek ActiveX do formularzy systemu Windows
Gdy Projektant formularzy systemu Windows jest zoptymalizowany do hosta formanty formularzy systemu Windows, można również wprowadzić formantów na formularzach systemu Windows.  
  
> [!CAUTION]
>  Istnieją ograniczenia dotyczące wydajności dla formularzy systemu Windows, po dodaniu formantów ActiveX do nich.  
  
 Przed dodaniem formantów ActiveX na formularzu, należy dodać je do przybornika. Aby uzyskać więcej informacji, zobacz [składników modelu COM, dostosowywanie przybornika — okno dialogowe](http://msdn.microsoft.com/en-us/171333f3-f207-4e02-bbdc-17862556212c).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>Aby dodać kontrolki ActiveX na formularzu systemu Windows  
  
-   Kliknij dwukrotnie formant w przyborniku.  
  
     [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]dodaje wszystkie odwołania do formantu w projekcie. Aby uzyskać więcej informacji dotyczących kwestii, które należy wziąć pod uwagę, gdy za pomocą formantów na formularzach systemu Windows, zobacz [uwagi odnośnie do hostowania kontrolki ActiveX na formularzu systemu Windows](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  Importer kontrolki ActiveX formularzy systemu Windows (AxImp.exe) tworzy argumenty zdarzeń innego typu niż oczekiwano na Import biblioteki dołączanej dynamicznie ActiveX. Argumenty utworzone przez AxImp.exe są podobne do następujących: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, gdy `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` jest oczekiwany. Należy pamiętać, że ta nieprawidłowości nie zapobiega kod działa prawidłowo. Aby uzyskać więcej informacji, zobacz [Importer kontrolki ActiveX formularzy systemu Windows (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Formanty formularzy systemu Windows](../../../../docs/framework/winforms/controls/index.md)  
 [Formanty i obiektów programowalnych w różnych językach i biblioteki](http://msdn.microsoft.com/en-us/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [Porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Rozmieszczanie formantów na formularzach systemu Windows](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Etykietowanie formantów formularzy systemu Windows poszczególnych i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Formanty do użycia w formularzach systemu Windows](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Formanty przez funkcję formularzy systemu Windows](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
