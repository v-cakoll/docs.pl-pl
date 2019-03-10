---
title: 'Instrukcje: Implementowanie interfejsu INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 51c0b1fa535921b7b33a16f55bdc8b76d6125e72
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57704092"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="ec336-102">Instrukcje: Implementowanie interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="ec336-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="ec336-103">Poniższy przykład kodu demonstruje sposób implementacji <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ec336-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="ec336-104">Implementuje ten interfejs na obiektach biznesowych, które są używane w powiązanie danych formularzy Windows.</span><span class="sxs-lookup"><span data-stu-id="ec336-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="ec336-105">Po wdrożeniu, interfejs komunikuje się kontrolki powiązane zmiany właściwości w obiekcie firmy.</span><span class="sxs-lookup"><span data-stu-id="ec336-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec336-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec336-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ec336-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec336-107">See also</span></span>
- [<span data-ttu-id="ec336-108">Instrukcje: Stosowanie wzorca PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="ec336-108">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="ec336-109">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec336-109">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="ec336-110">Instrukcje: Wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="ec336-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="ec336-111">Powiadomienie o zmianie w powiązaniu danych w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec336-111">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
