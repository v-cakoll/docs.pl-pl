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
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="b9e10-102">Instrukcje: dodawanie kontrolek ActiveX do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b9e10-102">How to: Add ActiveX Controls to Windows Forms</span></span>

<span data-ttu-id="b9e10-103">Gdy Windows Forms Designer w programie Visual Studio jest zoptymalizowany do kontrolek Windows Forms hosta, możesz umieścić formantów na formularzach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b9e10-103">While the Windows Forms Designer in Visual Studio is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>

> [!CAUTION]
> <span data-ttu-id="b9e10-104">Istnieją ograniczenia wydajności dla formularzy Windows Forms, podczas dodawania do nich kontrolki ActiveX.</span><span class="sxs-lookup"><span data-stu-id="b9e10-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>

<span data-ttu-id="b9e10-105">Przed dodaniem kontrolki ActiveX na formularzu, należy dodać je do przybornika.</span><span class="sxs-lookup"><span data-stu-id="b9e10-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="b9e10-106">Aby uzyskać więcej informacji, zobacz [składników modelu COM, dostosowywanie przybornika okno dialogowe](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b9e10-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>

## <a name="add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="b9e10-107">Dodawanie formantu ActiveX do formularza Windows</span><span class="sxs-lookup"><span data-stu-id="b9e10-107">Add an ActiveX control to your Windows Form</span></span>

<span data-ttu-id="b9e10-108">Aby dodać formant ActiveX do formularza Windows, kliknij dwukrotnie formant w przyborniku.</span><span class="sxs-lookup"><span data-stu-id="b9e10-108">To add an ActiveX control to your Windows Form, double-click the control on the Toolbox.</span></span>

<span data-ttu-id="b9e10-109">Visual Studio dodaje wszystkie odwołania do formantu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="b9e10-109">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="b9e10-110">Aby uzyskać więcej informacji na temat kwestii, które należy pamiętać, korzystając z formantów na formularzach Windows Forms, zobacz [uwagi odnośnie do hostowania kontrolki ActiveX na formularzu Windows](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="b9e10-110">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b9e10-111">Importer formantów ActiveX Windows Forms (AxImp.exe) tworzy argumenty zdarzeń innego typu niż oczekiwano na importowanie bibliotek dołączanych dynamicznie ActiveX.</span><span class="sxs-lookup"><span data-stu-id="b9e10-111">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="b9e10-112">Argumenty utworzone przez AxImp.exe są podobne do następujących: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, gdy `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` oczekuje.</span><span class="sxs-lookup"><span data-stu-id="b9e10-112">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="b9e10-113">Należy pamiętać, że ta nieprawidłowości nie uniemożliwia kod działa normalnie.</span><span class="sxs-lookup"><span data-stu-id="b9e10-113">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="b9e10-114">Aby uzyskać więcej informacji, zobacz [Importer kontrolki ActiveX formularzy Windows (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="b9e10-114">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b9e10-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9e10-115">See also</span></span>

- [<span data-ttu-id="b9e10-116">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9e10-116">Windows Forms Controls</span></span>](index.md)
- <span data-ttu-id="b9e10-117">[Formantów i programowanych obiektów w różnych językach i bibliotekach](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b9e10-117">[Controls and Programmable Objects Compared in Various Languages and Libraries](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))</span></span>
- [<span data-ttu-id="b9e10-118">Instrukcje: Dodawanie formantów do formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9e10-118">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="b9e10-119">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9e10-119">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="b9e10-120">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="b9e10-120">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="b9e10-121">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9e10-121">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="b9e10-122">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="b9e10-122">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
