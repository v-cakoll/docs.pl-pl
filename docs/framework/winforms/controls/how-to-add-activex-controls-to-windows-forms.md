---
title: 'Porady: dodawanie kontrolek ActiveX do formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: c851a215638e60642bf93564f4884b5a79d430d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Porady: dodawanie kontrolek ActiveX do formularzy systemu Windows
Gdy Projektant formularzy systemu Windows jest zoptymalizowany do hosta formanty formularzy systemu Windows, można również wprowadzić formantów na formularzach systemu Windows.  
  
> [!CAUTION]
>  Istnieją ograniczenia dotyczące wydajności dla formularzy systemu Windows, po dodaniu formantów ActiveX do nich.  
  
 Przed dodaniem formantów ActiveX na formularzu, należy dodać je do przybornika. Aby uzyskać więcej informacji, zobacz [składników modelu COM, dostosowywanie przybornika — okno dialogowe](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>Aby dodać kontrolki ActiveX na formularzu systemu Windows  
  
-   Kliknij dwukrotnie formant w przyborniku.  
  
     Visual Studio dodaje wszystkie odwołania do formantu w projekcie. Aby uzyskać więcej informacji dotyczących kwestii, które należy wziąć pod uwagę, gdy za pomocą formantów na formularzach systemu Windows, zobacz [uwagi odnośnie do hostowania kontrolki ActiveX na formularzu systemu Windows](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  Importer kontrolki ActiveX formularzy systemu Windows (AxImp.exe) tworzy argumenty zdarzeń innego typu niż oczekiwano na Import biblioteki dołączanej dynamicznie ActiveX. Argumenty utworzone przez AxImp.exe są podobne do następujących: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, gdy `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` jest oczekiwany. Należy pamiętać, że ta nieprawidłowości nie zapobiega kod działa prawidłowo. Aby uzyskać więcej informacji, zobacz [Importer kontrolki ActiveX formularzy systemu Windows (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Formanty i obiektów programowalnych w różnych językach i biblioteki](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
