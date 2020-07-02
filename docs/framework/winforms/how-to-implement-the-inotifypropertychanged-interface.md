---
title: 'Instrukcje: Implementowanie interfejsu INotifyPropertyChanged'
description: Dowiedz się, jak zaimplementować interfejs INotifyPropertyChanged na obiektach firmowych używanych w ramach powiązania danych Windows Forms.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 83d2ef32787d2dbcd877bc77dcede10111098f8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619271"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="65806-103">Instrukcje: Implementowanie interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="65806-103">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="65806-104">Poniższy przykład kodu demonstruje sposób implementacji <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="65806-104">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="65806-105">Zaimplementuj ten interfejs w obiektach firmowych, które są używane w ramach powiązania danych Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="65806-105">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="65806-106">Po zaimplementowaniu interfejs komunikuje się z kontrolką powiązaną ze zmianą właściwości w obiekcie biznesowym.</span><span class="sxs-lookup"><span data-stu-id="65806-106">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65806-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="65806-107">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="65806-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65806-108">See also</span></span>

- [<span data-ttu-id="65806-109">Instrukcje: Stosowanie wzorca PropertyNameChanged</span><span class="sxs-lookup"><span data-stu-id="65806-109">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="65806-110">Powiązywanie danych formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="65806-110">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="65806-111">Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="65806-111">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="65806-112">Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="65806-112">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
