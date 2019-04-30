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
ms.openlocfilehash: ffe4bf6fb29e82b04938e2ba9a2d9d21e5eabcde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747111"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a><span data-ttu-id="63970-102">Instrukcje: tworzenie klawiszy dostępu za pomocą kontrolek etykiet formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="63970-102">How to: Create Access Keys with Windows Forms Label Controls</span></span>
<span data-ttu-id="63970-103">Windows Forms <xref:System.Windows.Forms.Label> kontrolki mogą służyć do definiowania klucze dostępu dla innych kontrolek.</span><span class="sxs-lookup"><span data-stu-id="63970-103">Windows Forms <xref:System.Windows.Forms.Label> controls can be used to define access keys for other controls.</span></span> <span data-ttu-id="63970-104">Po zdefiniowaniu klucza dostępu w kontrolce etykiety, użytkownik może nacisnąć klawisz ALT i znak należy wyznaczyć, aby przenieść fokus do formantu, który po nim następuje w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="63970-104">When you define an access key in a label control, the user can press the ALT key plus the character you designate to move the focus to the control that follows it in the tab order.</span></span> <span data-ttu-id="63970-105">Ponieważ etykiety nie może otrzymać ostrości, automatycznie fokusu do następnej kontrolki w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="63970-105">Because labels cannot receive focus, focus automatically moves to the next control in the tab order.</span></span> <span data-ttu-id="63970-106">Użyj tej techniki, aby przypisać klucze dostępu do pola tekstowe, pola kombi, pola listy i siatek danych.</span><span class="sxs-lookup"><span data-stu-id="63970-106">Use this technique to assign access keys to text boxes, combo boxes, list boxes, and data grids.</span></span>  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a><span data-ttu-id="63970-107">Aby przypisać klucza dostępu do kontrolki z etykietą</span><span class="sxs-lookup"><span data-stu-id="63970-107">To assign an access key to a control with a label</span></span>  
  
1. <span data-ttu-id="63970-108">Najpierw rysować etykietę, a następnie narysuj inne kontrolki.</span><span class="sxs-lookup"><span data-stu-id="63970-108">Draw the label first, and then draw the other control.</span></span>  
  
     <span data-ttu-id="63970-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="63970-109">-or-</span></span>  
  
     <span data-ttu-id="63970-110">Rysowanie kontrolki w dowolnej kolejności i ustaw <xref:System.Windows.Forms.Control.TabIndex%2A> właściwość etykiety na mniejszej o jeden od innego formantu.</span><span class="sxs-lookup"><span data-stu-id="63970-110">Draw the controls in any order and set the <xref:System.Windows.Forms.Control.TabIndex%2A> property of the label to one less than the other control.</span></span>  
  
2. <span data-ttu-id="63970-111">Ustaw właściwość etykiety <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="63970-111">Set the label's <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`.</span></span>  
  
3. <span data-ttu-id="63970-112">Użyj handlowe "i" (&) na etykiecie <xref:System.Windows.Forms.Label.Text%2A> właściwości, aby przypisać klucz dostępu dla etykiety.</span><span class="sxs-lookup"><span data-stu-id="63970-112">Use an ampersand (&) in the label's <xref:System.Windows.Forms.Label.Text%2A> property to assign the access key for the label.</span></span> <span data-ttu-id="63970-113">Aby uzyskać więcej informacji, zobacz [tworzenia kluczy dla Windows Forms kontroli dostępu](how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="63970-113">For more information, see [Creating Access Keys for Windows Forms Controls](how-to-create-access-keys-for-windows-forms-controls.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="63970-114">Możesz chcieć wyświetlić takie znaki w kontrolce etykiety, a nie umożliwia tworzenie klawiszy dostępu.</span><span class="sxs-lookup"><span data-stu-id="63970-114">You may want to display ampersands in a label control, rather than use them to create access keys.</span></span> <span data-ttu-id="63970-115">Może to nastąpić, gdy powiąże formant etykiety do pola w zestawie rekordów, w którym dane obejmują takie znaki.</span><span class="sxs-lookup"><span data-stu-id="63970-115">This may occur if you bind a label control to a field in a recordset where the data includes ampersands.</span></span> <span data-ttu-id="63970-116">Aby wyświetlić takie znaki w kontrolce etykiety, należy ustawić <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="63970-116">To display ampersands in a label control, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `false`.</span></span> <span data-ttu-id="63970-117">Jeśli chcesz wyświetlić takie znaki i mają klucz dostępu, ustaw <xref:System.Windows.Forms.Label.UseMnemonic%2A> właściwość `true` i wskazuje klucz dostępu za pomocą jednego handlowe "i" (&) i handlowe "i", aby wyświetlić z dwa takie znaki.</span><span class="sxs-lookup"><span data-stu-id="63970-117">If you wish to display ampersands and also have an access key, set the <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true` and indicate the access key with one ampersand (&) and the ampersand to display with two ampersands.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="63970-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63970-118">See also</span></span>

- [<span data-ttu-id="63970-119">Instrukcje: Rozmiaru kontrolki Label formularzy Windows pasujący do jego zawartości</span><span class="sxs-lookup"><span data-stu-id="63970-119">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [<span data-ttu-id="63970-120">Label, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="63970-120">Label Control Overview</span></span>](label-control-overview-windows-forms.md)
- [<span data-ttu-id="63970-121">Label, kontrolka</span><span class="sxs-lookup"><span data-stu-id="63970-121">Label Control</span></span>](label-control-windows-forms.md)
