---
title: 'Instrukcje: dodawanie w sposób programowy elementów do kontrolki DomainUpDown formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- spin button control [Windows Forms], adding items
- DomainUpDown control [Windows Forms], adding items to
ms.assetid: fd31d314-33eb-4181-90f8-d32ed0c4e072
ms.openlocfilehash: 32f58dc8b8b96a3d8660550d8ce7696839587ddc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080673"
---
# <a name="how-to-add-items-to-windows-forms-domainupdown-controls-programmatically"></a><span data-ttu-id="a12ec-102">Instrukcje: dodawanie w sposób programowy elementów do kontrolki DomainUpDown formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a12ec-102">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>
<span data-ttu-id="a12ec-103">Można dodać elementy do formularzy Windows Forms <xref:System.Windows.Forms.DomainUpDown> kontrolki w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a12ec-103">You can add items to the Windows Forms <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span> <span data-ttu-id="a12ec-104">Wywołaj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> lub <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metody <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> klasy do dodawania elementów do formantu <xref:System.Windows.Forms.DomainUpDown.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="a12ec-104">Call the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> or <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method of the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection> class to add items to the control's <xref:System.Windows.Forms.DomainUpDown.Items%2A> property.</span></span> <span data-ttu-id="a12ec-105"><xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> Metoda dodaje element do końca kolekcji, podczas gdy <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metoda dodaje element na określonej pozycji.</span><span class="sxs-lookup"><span data-stu-id="a12ec-105">The <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method adds an item to the end of a collection, while the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method adds an item at a specified position.</span></span>  
  
### <a name="to-add-a-new-item"></a><span data-ttu-id="a12ec-106">Aby dodać nowy element</span><span class="sxs-lookup"><span data-stu-id="a12ec-106">To add a new item</span></span>  
  
1.  <span data-ttu-id="a12ec-107">Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> metodę, aby dodać element do końca listy elementów.</span><span class="sxs-lookup"><span data-stu-id="a12ec-107">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A> method to add an item to the end of the list of items.</span></span>  
  
    ```vb  
    DomainUpDown1.Items.Add("noodles")  
    ```  
  
    ```csharp  
    domainUpDown1.Items.Add("noodles");  
    ```  
  
    ```cpp  
    domainUpDown1->Items->Add("noodles");  
    ```  
  
     <span data-ttu-id="a12ec-108">—lub—</span><span class="sxs-lookup"><span data-stu-id="a12ec-108">-or-</span></span>  
  
2.  <span data-ttu-id="a12ec-109">Użyj <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> metodę, aby wstawić element do listy na określonej pozycji.</span><span class="sxs-lookup"><span data-stu-id="a12ec-109">Use the <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Insert%2A> method to insert an item into the list at a specified position.</span></span>  
  
    ```vb  
    ' Inserts an item at the third position in the list  
    DomainUpDown1.Items.Insert(2, "rice")  
    ```  
  
    ```csharp  
    // Inserts an item at the third position in the list  
    domainUpDown1.Items.Insert(2, "rice");  
    ```  
  
    ```cpp  
    // Inserts an item at the third position in the list  
    domainUpDown1->Items->Insert(2, "rice");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a12ec-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a12ec-110">See also</span></span>

- <xref:System.Windows.Forms.DomainUpDown>
- <xref:System.Windows.Forms.DomainUpDown.DomainUpDownItemCollection.Add%2A?displayProperty=nameWithType>
- <xref:System.Collections.ArrayList.Insert%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a12ec-111">DomainUpDown, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a12ec-111">DomainUpDown Control</span></span>](domainupdown-control-windows-forms.md)
- [<span data-ttu-id="a12ec-112">DomainUpDown, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a12ec-112">DomainUpDown Control Overview</span></span>](domainupdown-control-overview-windows-forms.md)
