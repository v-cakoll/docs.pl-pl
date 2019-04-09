---
title: 'Instrukcje: dodawanie kontrolek ActiveX do formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 780411949c543a2178de5e7c531bd2202703f27a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166053"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Instrukcje: dodawanie kontrolek ActiveX do formularzy systemu Windows
Gdy Windows Forms Designer jest zoptymalizowany do kontrolek Windows Forms hosta, możesz umieścić formantów na formularzach Windows Forms.  
  
> [!CAUTION]
>  Istnieją ograniczenia wydajności dla formularzy Windows Forms, podczas dodawania do nich kontrolki ActiveX.  
  
 Przed dodaniem kontrolki ActiveX na formularzu, należy dodać je do przybornika. Aby uzyskać więcej informacji, zobacz [składników modelu COM, dostosowywanie przybornika okno dialogowe](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a>Aby dodać formant ActiveX do formularza Windows  
  
-   Kliknij dwukrotnie formant w przyborniku.  
  
     Visual Studio dodaje wszystkie odwołania do formantu w projekcie. Aby uzyskać więcej informacji na temat kwestii, które należy pamiętać, korzystając z formantów na formularzach Windows Forms, zobacz [uwagi odnośnie do hostowania kontrolki ActiveX na formularzu Windows](considerations-when-hosting-an-activex-control-on-a-windows-form.md).  
  
    > [!NOTE]
    >  Importer formantów ActiveX Windows Forms (AxImp.exe) tworzy argumenty zdarzeń innego typu niż oczekiwano na importowanie bibliotek dołączanych dynamicznie ActiveX. Argumenty utworzone przez AxImp.exe są podobne do następujących: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, gdy `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` oczekuje. Należy pamiętać, że ta nieprawidłowości nie uniemożliwia kod działa normalnie. Aby uzyskać więcej informacji, zobacz [Importer kontrolki ActiveX formularzy Windows (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).  
  
## <a name="see-also"></a>Zobacz także

- [Formanty formularzy systemu Windows](index.md)
- [Porównanie formantów i programowanych obiektów w różnych językach i bibliotekach](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Instrukcje: dodawanie kontrolek do formularzy systemu Windows](how-to-add-controls-to-windows-forms.md)
- [Rozmieszczanie formantów na formularzach systemu Windows](arranging-controls-on-windows-forms.md)
- [Etykietowanie pojedynczych formantów formularzy systemu Windows i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
- [Formanty formularzy systemu Windows według funkcji](windows-forms-controls-by-function.md)
