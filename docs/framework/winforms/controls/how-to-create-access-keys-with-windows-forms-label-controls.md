---
title: 'Instrukcje: tworzenie klawiszy dostępu za pomocą kontrolek etykiet formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
ms.openlocfilehash: dd7f238f8c20ba990158f23344e36376d3b1cb7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950537"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="497cf-102">Instrukcje: tworzenie klawiszy dostępu za pomocą kontrolek etykiet formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="497cf-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="497cf-103">Kontrolki Windows Forms <xref:System.Windows.Forms.Label> mogą służyć do definiowania kluczy dostępu dla innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="497cf-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="497cf-104">Po zdefiniowaniu klucza dostępu w kontrolce etykieta, użytkownik może nacisnąć klawisz ALT i znak, aby przenieść fokus do kontrolki, która następuje po niej w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="497cf-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="497cf-105">Ponieważ etykiety nie mogą odbierać fokusu, fokus jest automatycznie przenoszony do następnego formantu w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="497cf-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="497cf-106">Ta technika służy do przypisywania kluczy dostępu do pól tekstowych, pól kombi, pól listy i siatek danych.</span><span class="sxs-lookup"><span data-stu-id="497cf-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="497cf-107">Aby przypisać klucz dostępu do kontrolki z etykietą</span><span class="sxs-lookup"><span data-stu-id="497cf-107">To assign an access key to a control with a label</span></span>  
  
1. <span data-ttu-id="497cf-108">Najpierw narysuj etykietę, a następnie narysuj drugą kontrolkę.</span><span class="sxs-lookup"><span data-stu-id="497cf-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="497cf-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="497cf-109">-or-</span></span>  
  
     <span data-ttu-id="497cf-110">Narysuj kontrolki w dowolnej kolejności i ustaw <xref:System.Windows.Forms.Control.TabIndex%2A> właściwość etykiety na mniejszą niż inna kontrolka.</span><span class="sxs-lookup"><span data-stu-id="497cf-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2. <span data-ttu-id="497cf-111">Ustaw <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość etykiety na `true`wartość.</span><span class="sxs-lookup"><span data-stu-id="497cf-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="497cf-112">Użyj znaku handlowego "i" (&) we <xref:System.Windows.Forms.Label.Text%2A> właściwości etykiety, aby przypisać klucz dostępu dla etykiety.</span><span class="sxs-lookup"><span data-stu-id="497cf-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="497cf-113">Aby uzyskać więcej informacji, zobacz [Tworzenie kluczy dostępu dla formantów Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="497cf-113">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="497cf-114">W kontrolce etykieta można wyświetlić znaki handlowe zamiast używać ich do tworzenia kluczy dostępu.</span><span class="sxs-lookup"><span data-stu-id="497cf-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="497cf-115">Taka sytuacja może wystąpić, jeśli powiążesz kontrolkę etykieta z polem w zestawie rekordów, gdzie dane zawierają znak handlowego "i".</span><span class="sxs-lookup"><span data-stu-id="497cf-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="497cf-116">Aby wyświetlić znaki handlowe w kontrolce etykieta, ustaw <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość na. `false`</span><span class="sxs-lookup"><span data-stu-id="497cf-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="497cf-117">Jeśli chcesz wyświetlić znak handlowego "i" także klucz dostępu, ustaw <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość na `true` i wskaż klucz dostępu z jednym znakiem & handlowego "i", aby wyświetlić z dwoma znakami "i".</span><span class="sxs-lookup"><span data-stu-id="497cf-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="497cf-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="497cf-118">See also</span></span>

- [<span data-ttu-id="497cf-119">Instrukcje: Dopasuj rozmiar kontrolki etykiety Windows Forms do jej zawartości</span><span class="sxs-lookup"><span data-stu-id="497cf-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="497cf-120">Label, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="497cf-120">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="497cf-121">Label, kontrolka</span><span class="sxs-lookup"><span data-stu-id="497cf-121">Label Control</span></span>](label-control-windows-forms.md)
