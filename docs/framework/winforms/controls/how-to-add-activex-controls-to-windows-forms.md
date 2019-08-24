---
title: 'Instrukcje: dodawanie kontrolek ActiveX do formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 8c4c6c3f96c49401b032e360314794cc800c0551
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69987067"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a>Instrukcje: dodawanie kontrolek ActiveX do formularzy systemu Windows

Gdy Projektant formularzy systemu Windows w programie Visual Studio jest zoptymalizowany pod kątem hostowania Windows Forms formantów, można również umieścić kontrolki ActiveX w Windows Forms.

> [!CAUTION]
> Istnieją ograniczenia wydajności Windows Forms, gdy do nich są dodawane kontrolki ActiveX.

Przed dodaniem formantów ActiveX do formularza, należy dodać je do przybornika. Aby uzyskać więcej informacji, zobacz [składniki com, Dostosowywanie przybornika okna dialogowego](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).

## <a name="add-an-activex-control-to-your-windows-form"></a>Dodawanie kontrolki ActiveX do formularza systemu Windows

Aby dodać kontrolkę ActiveX do formularza systemu Windows, kliknij dwukrotnie formant w przyborniku.

Program Visual Studio dodaje wszystkie odwołania do formantu w projekcie. Aby uzyskać więcej informacji o zagadnieniach, które należy wziąć pod uwagę podczas korzystania z formantów ActiveX na Windows Forms, zobacz [uwagi dotyczące hostowania kontrolki ActiveX w formularzu systemu Windows](considerations-when-hosting-an-activex-control-on-a-windows-form.md).

> [!NOTE]
> Windows Forms importer kontrolki ActiveX (AxImp. exe) tworzy argumenty zdarzenia innego typu niż oczekiwano przy przywozie bibliotek dołączanych dynamicznie ActiveX. Argumenty utworzone przez Aximp. exe są podobne do następujących: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, gdy `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` jest oczekiwany. Należy pamiętać, że taka nieprawidłowość nie zapobiega normalnemu działaniu kodu. Aby uzyskać szczegółowe informacje, zobacz [Windows Forms importer formantów ActiveX (Aximp. exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Formanty i obiekty programowalne porównane w różnych językach i bibliotekach](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [Instrukcje: Dodawanie formantów do Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
