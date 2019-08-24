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
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="2c250-102">Instrukcje: dodawanie kontrolek ActiveX do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2c250-102">How to: Add ActiveX Controls to Windows Forms</span></span>

<span data-ttu-id="2c250-103">Gdy Projektant formularzy systemu Windows w programie Visual Studio jest zoptymalizowany pod kątem hostowania Windows Forms formantów, można również umieścić kontrolki ActiveX w Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2c250-103">While the Windows Forms Designer in Visual Studio is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>

> [!CAUTION]
> <span data-ttu-id="2c250-104">Istnieją ograniczenia wydajności Windows Forms, gdy do nich są dodawane kontrolki ActiveX.</span><span class="sxs-lookup"><span data-stu-id="2c250-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>

<span data-ttu-id="2c250-105">Przed dodaniem formantów ActiveX do formularza, należy dodać je do przybornika.</span><span class="sxs-lookup"><span data-stu-id="2c250-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="2c250-106">Aby uzyskać więcej informacji, zobacz [składniki com, Dostosowywanie przybornika okna dialogowego](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2c250-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>

## <a name="add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="2c250-107">Dodawanie kontrolki ActiveX do formularza systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2c250-107">Add an ActiveX control to your Windows Form</span></span>

<span data-ttu-id="2c250-108">Aby dodać kontrolkę ActiveX do formularza systemu Windows, kliknij dwukrotnie formant w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="2c250-108">To add an ActiveX control to your Windows Form, double-click the control on the Toolbox.</span></span>

<span data-ttu-id="2c250-109">Program Visual Studio dodaje wszystkie odwołania do formantu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="2c250-109">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="2c250-110">Aby uzyskać więcej informacji o zagadnieniach, które należy wziąć pod uwagę podczas korzystania z formantów ActiveX na Windows Forms, zobacz [uwagi dotyczące hostowania kontrolki ActiveX w formularzu systemu Windows](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="2c250-110">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>

> [!NOTE]
> <span data-ttu-id="2c250-111">Windows Forms importer kontrolki ActiveX (AxImp. exe) tworzy argumenty zdarzenia innego typu niż oczekiwano przy przywozie bibliotek dołączanych dynamicznie ActiveX.</span><span class="sxs-lookup"><span data-stu-id="2c250-111">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="2c250-112">Argumenty utworzone przez Aximp. exe są podobne do następujących: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, gdy `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` jest oczekiwany.</span><span class="sxs-lookup"><span data-stu-id="2c250-112">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="2c250-113">Należy pamiętać, że taka nieprawidłowość nie zapobiega normalnemu działaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="2c250-113">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="2c250-114">Aby uzyskać szczegółowe informacje, zobacz [Windows Forms importer formantów ActiveX (Aximp. exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="2c250-114">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c250-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c250-115">See also</span></span>

- [<span data-ttu-id="2c250-116">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c250-116">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="2c250-117">[Formanty i obiekty programowalne porównane w różnych językach i bibliotekach](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2c250-117">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="2c250-118">Instrukcje: Dodawanie formantów do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c250-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="2c250-119">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="2c250-119">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="2c250-120">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2c250-120">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="2c250-121">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="2c250-121">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
