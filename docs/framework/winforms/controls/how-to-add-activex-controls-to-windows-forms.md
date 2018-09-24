---
title: 'Porady: dodawanie kontrolek ActiveX do formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 7d6514c679187e9ec193f6dda8336c8bd56fac81
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2018
ms.locfileid: "46706321"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Porady: dodawanie kontrolek ActiveX do formularzy systemu Windows
Gdy Windows Forms Designer jest zoptymalizowany do kontrolek Windows Forms hosta, możesz umieścić formantów na formularzach Windows Forms.  
  
> [!CAUTION]
>  Istnieją ograniczenia wydajności dla formularzy Windows Forms, podczas dodawania do nich kontrolki ActiveX.  
  
 Przed dodaniem kontrolki ActiveX na formularzu, należy dodać je do przybornika. Aby uzyskać więcej informacji, zobacz [składników modelu COM, dostosowywanie przybornika okno dialogowe](https://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>Aby dodać formant ActiveX do formularza Windows  
  
-   Kliknij dwukrotnie formant w przyborniku.  
  
     Visual Studio dodaje wszystkie odwołania do formantu w projekcie. Aby uzyskać więcej informacji na temat kwestii, które należy pamiętać, korzystając z formantów na formularzach Windows Forms, zobacz [uwagi odnośnie do hostowania kontrolki ActiveX na formularzu Windows](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  Importer formantów ActiveX Windows Forms (AxImp.exe) tworzy argumenty zdarzeń innego typu niż oczekiwano na importowanie bibliotek dołączanych dynamicznie ActiveX. Argumenty utworzone przez AxImp.exe są podobne do następujących: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, gdy `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` oczekuje. Należy pamiętać, że ta nieprawidłowości nie uniemożliwia kod działa normalnie. Aby uzyskać więcej informacji, zobacz [Importer kontrolki ActiveX formularzy Windows (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Formantów i programowanych obiektów w różnych językach i bibliotekach](https://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [Instrukcje: dodawanie kontrolek do formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
