---
title: Zachowanie AutoSize w formancie TableLayoutPanel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- localizing forms
- layout [Windows Forms], AutoSize
- sizing [Windows Forms], automatic
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- automatic sizing
- AutoSizeMode property
ms.assetid: 9233e0c3-2fa6-405e-8701-959479b1250e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06bd0686b31b52ccb8580a545910339d2e2cd5bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="autosize-behavior-in-the-tablelayoutpanel-control"></a><span data-ttu-id="336c5-102">Zachowanie AutoSize w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="336c5-102">AutoSize Behavior in the TableLayoutPanel Control</span></span>
## <a name="distinct-autosize-behaviors"></a><span data-ttu-id="336c5-103">AutoSize różne zachowania</span><span class="sxs-lookup"><span data-stu-id="336c5-103">Distinct AutoSize Behaviors</span></span>  
 <span data-ttu-id="336c5-104"><xref:System.Windows.Forms.TableLayoutPanel> Sterowanie obsługuje zachowanie automatycznej zmiany rozmiaru w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="336c5-104">The <xref:System.Windows.Forms.TableLayoutPanel> control supports automatic sizing behavior in the following ways:</span></span>  
  
-   <span data-ttu-id="336c5-105">Za pomocą <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości;</span><span class="sxs-lookup"><span data-stu-id="336c5-105">Through the <xref:System.Windows.Forms.Control.AutoSize%2A> property;</span></span>  
  
-   <span data-ttu-id="336c5-106">Za pomocą <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość <xref:System.Windows.Forms.TableLayoutPanel> formantu Style kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="336c5-106">Through the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property on the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
### <a name="the-autosize-property-with-row-and-column-styles"></a><span data-ttu-id="336c5-107">AutoSize właściwość Style kolumn i wierszy</span><span class="sxs-lookup"><span data-stu-id="336c5-107">The AutoSize Property with Row and Column Styles</span></span>  
 <span data-ttu-id="336c5-108">W poniższej tabeli opisano interakcje między <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości i <xref:System.Windows.Forms.TableLayoutPanel> formantu Style kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="336c5-108">The following table describes the interaction between the <xref:System.Windows.Forms.Control.AutoSize%2A> property and the <xref:System.Windows.Forms.TableLayoutPanel> control’s column and row styles.</span></span>  
  
|<span data-ttu-id="336c5-109">Ustawienia automatycznego dopasowania rozmiaru</span><span class="sxs-lookup"><span data-stu-id="336c5-109">AutoSize setting</span></span>|<span data-ttu-id="336c5-110">Styl interakcji</span><span class="sxs-lookup"><span data-stu-id="336c5-110">Style interaction</span></span>|  
|----------------------|-----------------------|  
|`false`|<span data-ttu-id="336c5-111"><xref:System.Windows.Forms.TableLayoutPanel> Formant przechodzi od lewej do prawej i przydziela miejsce dla kolumny lub wiersza lub w następującej kolejności.</span><span class="sxs-lookup"><span data-stu-id="336c5-111">The <xref:System.Windows.Forms.TableLayoutPanel> control proceeds from left to right, and allocates space for the column or row or in the following order.</span></span><br /><br /> <span data-ttu-id="336c5-112">1.  Jeśli <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.SizeType.Absolute>, liczbę pikseli określone przez <xref:System.Windows.Forms.ColumnStyle.Width%2A> lub <xref:System.Windows.Forms.RowStyle.Height%2A> został przydzielony.</span><span class="sxs-lookup"><span data-stu-id="336c5-112">1.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.Absolute>, the number of pixels specified by <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> is allocated.</span></span><br /><span data-ttu-id="336c5-113">2.  Jeśli <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.SizeType.AutoSize>, zwracane przez formant podrzędny w pikselach <xref:System.Windows.Forms.Control.GetPreferredSize%2A> metody został przydzielony.</span><span class="sxs-lookup"><span data-stu-id="336c5-113">2.  If the <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> property is set to <xref:System.Windows.Forms.SizeType.AutoSize>, the number of pixels returned by the child control’s <xref:System.Windows.Forms.Control.GetPreferredSize%2A> method is allocated.</span></span><br /><span data-ttu-id="336c5-114">3.  Po miejsca dla wszystkich <xref:System.Windows.Forms.SizeType.Absolute> i <xref:System.Windows.Forms.SizeType.AutoSize> kolumn lub wierszy jest przydzielona, wszystkie kolumny lub wiersze z <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> ustawioną <xref:System.Windows.Forms.SizeType.Percent> służą do proporcjonalnie przydzielić pozostałej ilości wolnego miejsca</span><span class="sxs-lookup"><span data-stu-id="336c5-114">3.  After space for all <xref:System.Windows.Forms.SizeType.Absolute> and <xref:System.Windows.Forms.SizeType.AutoSize> columns or rows is allocated, any columns or rows with <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> set to <xref:System.Windows.Forms.SizeType.Percent> are used to proportionally allocate the remaining free space</span></span>|  
|`true`|<span data-ttu-id="336c5-115">Podobnie jak poprzednie interakcji, z wyjątkiem tego, który <xref:System.Windows.Forms.SizeType.Percent> kolumn lub wierszy uzyskać aspekt automatycznej zmiany rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="336c5-115">Similar to the previous interaction, with the exception that <xref:System.Windows.Forms.SizeType.Percent> columns or rows acquire an automatic sizing aspect.</span></span><br /><br /> <span data-ttu-id="336c5-116"><xref:System.Windows.Forms.TableLayoutPanel> Kontroli rozszerza kolumny lub wiersza, aby utworzyć odpowiednią ilością wolnego miejsca, aby nie kolumny lub wiersza z <xref:System.Windows.Forms.SizeType.Percent> stylów klipy jego zawartość.</span><span class="sxs-lookup"><span data-stu-id="336c5-116">The <xref:System.Windows.Forms.TableLayoutPanel> control expands the column or row to create adequate free space, so that no column or row with <xref:System.Windows.Forms.SizeType.Percent> styling clips its contents.</span></span> <span data-ttu-id="336c5-117"><xref:System.Windows.Forms.TableLayoutPanel> Kontroli przydziela nowe miejsce proporcjonalnie zgodnie z <xref:System.Windows.Forms.ColumnStyle.Width%2A> lub <xref:System.Windows.Forms.RowStyle.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="336c5-117">The <xref:System.Windows.Forms.TableLayoutPanel> control allocates the new space proportionally according to the <xref:System.Windows.Forms.ColumnStyle.Width%2A> or <xref:System.Windows.Forms.RowStyle.Height%2A> property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="336c5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="336c5-118">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="336c5-119">TableLayoutPanel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="336c5-119">TableLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-overview.md)
