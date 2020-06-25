---
title: 'Porady: wyświetlanie godziny za pomocą formantu DateTimePicker'
description: Dowiedz się, jak używać formantu DateTimePicker Windows Forms, aby umożliwić użytkownikom wybranie daty i godziny oraz wyświetlanie daty i godziny w określonym formacie.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: ab584367a189d05e567bb57d386c6bf629201102
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325584"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a><span data-ttu-id="c3de2-103">Porady: wyświetlanie godziny za pomocą formantu DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="c3de2-103">How to: Display Time with the DateTimePicker Control</span></span>
<span data-ttu-id="c3de2-104">Jeśli chcesz, aby aplikacja umożliwiała użytkownikom wybranie daty i godziny oraz wyświetlenie daty i godziny w określonym formacie, użyj <xref:System.Windows.Forms.DateTimePicker> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c3de2-104">If you want your application to enable users to select a date and time, and to display that date and time in the specified format, use the <xref:System.Windows.Forms.DateTimePicker> control.</span></span> <span data-ttu-id="c3de2-105">Poniższa procedura pokazuje, jak używać <xref:System.Windows.Forms.DateTimePicker> kontrolki do wyświetlania czasu.</span><span class="sxs-lookup"><span data-stu-id="c3de2-105">The following procedure shows how to use the <xref:System.Windows.Forms.DateTimePicker> control to display the time.</span></span>  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a><span data-ttu-id="c3de2-106">Aby wyświetlić czas z kontrolką DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="c3de2-106">To display the time with the DateTimePicker control</span></span>  
  
1. <span data-ttu-id="c3de2-107">Ustaw <xref:System.Windows.Forms.DateTimePicker.Format%2A> Właściwość na<xref:System.Windows.Forms.DateTimePickerFormat.Time></span><span class="sxs-lookup"><span data-stu-id="c3de2-107">Set the <xref:System.Windows.Forms.DateTimePicker.Format%2A> property to <xref:System.Windows.Forms.DateTimePickerFormat.Time></span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. <span data-ttu-id="c3de2-108">Ustaw <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> Właściwość na <xref:System.Windows.Forms.DateTimePicker> `true` .</span><span class="sxs-lookup"><span data-stu-id="c3de2-108">Set the <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> property for the <xref:System.Windows.Forms.DateTimePicker> to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="c3de2-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3de2-109">Example</span></span>  
 <span data-ttu-id="c3de2-110">Poniższy przykład kodu pokazuje, jak utworzyć element <xref:System.Windows.Forms.DateTimePicker> , który umożliwia użytkownikom wybranie tylko czasu.</span><span class="sxs-lookup"><span data-stu-id="c3de2-110">The following code sample shows how to create a <xref:System.Windows.Forms.DateTimePicker> that enables users to choose a time only.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c3de2-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c3de2-111">Compiling the Code</span></span>  
 <span data-ttu-id="c3de2-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c3de2-112">This example requires:</span></span>  
  
- <span data-ttu-id="c3de2-113">Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="c3de2-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3de2-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3de2-114">See also</span></span>

- [<span data-ttu-id="c3de2-115">DateTimePicker, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c3de2-115">DateTimePicker Control</span></span>](datetimepicker-control-windows-forms.md)
