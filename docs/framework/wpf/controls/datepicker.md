---
title: DatePicker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd5c7c796ee9d51a216368de3f3b04c10a5a3acd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="datepicker"></a><span data-ttu-id="f6692-102">DatePicker</span><span class="sxs-lookup"><span data-stu-id="f6692-102">DatePicker</span></span>
<span data-ttu-id="f6692-103"><xref:System.Windows.Controls.DatePicker> Kontroli zezwala użytkownikowi na wybranie daty, wpisując albo go do pola tekstowego lub za pomocą listy rozwijanej <xref:System.Windows.Controls.Calendar> formantu.</span><span class="sxs-lookup"><span data-stu-id="f6692-103">The <xref:System.Windows.Controls.DatePicker> control allows the user to select a date by either typing it into a text field or by using a drop-down <xref:System.Windows.Controls.Calendar> control.</span></span>  
  
 <span data-ttu-id="f6692-104">Na poniższej ilustracji pokazano <xref:System.Windows.Controls.DatePicker>.</span><span class="sxs-lookup"><span data-stu-id="f6692-104">The following illustration shows a <xref:System.Windows.Controls.DatePicker>.</span></span>  
  
 <span data-ttu-id="f6692-105">![Formant selektora daty](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span><span class="sxs-lookup"><span data-stu-id="f6692-105">![DatePicker control](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span></span>  
<span data-ttu-id="f6692-106">Formant selektora daty</span><span class="sxs-lookup"><span data-stu-id="f6692-106">DatePicker Control</span></span>  
  
 <span data-ttu-id="f6692-107">Duża liczba <xref:System.Windows.Controls.DatePicker> są właściwości formantu w zarządzaniu wbudowanych <xref:System.Windows.Controls.Calendar>i działają tak samo jak równoważne właściwości w <xref:System.Windows.Controls.Calendar>.</span><span class="sxs-lookup"><span data-stu-id="f6692-107">Many of a <xref:System.Windows.Controls.DatePicker> control's properties are for managing its built-in <xref:System.Windows.Controls.Calendar>, and function identically to the equivalent property in <xref:System.Windows.Controls.Calendar>.</span></span> <span data-ttu-id="f6692-108">W szczególności <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, i <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> właściwości działania tak samo do ich <xref:System.Windows.Controls.Calendar> odpowiedniki.</span><span class="sxs-lookup"><span data-stu-id="f6692-108">In particular, the <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, and <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> properties function identically to their <xref:System.Windows.Controls.Calendar> counterparts.</span></span> <span data-ttu-id="f6692-109">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.Calendar>.</span><span class="sxs-lookup"><span data-stu-id="f6692-109">For more information, see <xref:System.Windows.Controls.Calendar>.</span></span>  
  
 <span data-ttu-id="f6692-110">Użytkownicy mogą wpisywać daty bezpośrednio do pola tekstowego, który określa <xref:System.Windows.Controls.DatePicker.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f6692-110">Users can type a date directly into a text field, which sets the <xref:System.Windows.Controls.DatePicker.Text%2A> property.</span></span> <span data-ttu-id="f6692-111">Jeśli <xref:System.Windows.Controls.DatePicker> nie można przekonwertować ciągu wprowadzone na prawidłową datę <xref:System.Windows.Controls.DatePicker.DateValidationError> zdarzeń zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="f6692-111">If the <xref:System.Windows.Controls.DatePicker> cannot convert the entered string to a valid date, the <xref:System.Windows.Controls.DatePicker.DateValidationError> event will be raised.</span></span> <span data-ttu-id="f6692-112">Domyślnie powoduje to wyjątek, ale program obsługi zdarzeń dla <xref:System.Windows.Controls.DatePicker.DateValidationError> można ustawić <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> właściwości `false` i zapobiec zgłaszanych wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f6692-112">By default, this causes an exception, but an event handler for <xref:System.Windows.Controls.DatePicker.DateValidationError> can set the <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> property to `false` and prevent an exception from being raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6692-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6692-113">See Also</span></span>  
 [<span data-ttu-id="f6692-114">Formanty</span><span class="sxs-lookup"><span data-stu-id="f6692-114">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
 [<span data-ttu-id="f6692-115">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="f6692-115">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
