---
title: 'Instrukcje: dodawanie kontrolek ActiveX do formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 17311adade187ef3c8e4e639299e6c5cbbcd98a9
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210391"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Instrukcje: dodawanie kontrolek ActiveX do formularzy systemu Windows

Gdy Windows Forms Designer w programie Visual Studio jest zoptymalizowany do kontrolek Windows Forms hosta, możesz umieścić formantów na formularzach Windows Forms.

> [!CAUTION]
> Istnieją ograniczenia wydajności dla formularzy Windows Forms, podczas dodawania do nich kontrolki ActiveX.

Przed dodaniem kontrolki ActiveX na formularzu, należy dodać je do przybornika. Aby uzyskać więcej informacji, zobacz [składników modelu COM, dostosowywanie przybornika okno dialogowe](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).

## <a name="add-an-activex-control-to-your-windows-form"></a>Dodawanie formantu ActiveX do formularza Windows

Aby dodać formant ActiveX do formularza Windows, kliknij dwukrotnie formant w przyborniku.

Visual Studio dodaje wszystkie odwołania do formantu w projekcie. Aby uzyskać więcej informacji na temat kwestii, które należy pamiętać, korzystając z formantów na formularzach Windows Forms, zobacz [uwagi odnośnie do hostowania kontrolki ActiveX na formularzu Windows](considerations-when-hosting-an-activex-control-on-a-windows-form.md).

> [!NOTE]
> Importer formantów ActiveX Windows Forms (AxImp.exe) tworzy argumenty zdarzeń innego typu niż oczekiwano na importowanie bibliotek dołączanych dynamicznie ActiveX. Argumenty utworzone przez AxImp.exe są podobne do następujących: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, gdy `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` oczekuje. Należy pamiętać, że ta nieprawidłowości nie uniemożliwia kod działa normalnie. Aby uzyskać więcej informacji, zobacz [Importer kontrolki ActiveX formularzy Windows (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Formantów i programowanych obiektów w różnych językach i bibliotekach](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Instrukcje: Dodawanie formantów do formularzy Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Rozmieszczanie kontrolek na formularzach Windows Forms](arranging-controls-on-windows-forms.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
