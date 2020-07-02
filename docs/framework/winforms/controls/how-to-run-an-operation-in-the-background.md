---
title: 'Porady: uruchamianie operacji w tle'
description: Dowiedz się, jak używać klasy BackgroundWorker do uruchamiania czasochłonnej operacji Windows Forms w tle.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
ms.openlocfilehash: 6b2a97f5acf1e906dfe141aee62e99a4e50dca9f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621577"
---
# <a name="how-to-run-an-operation-in-the-background"></a><span data-ttu-id="95505-103">Porady: uruchamianie operacji w tle</span><span class="sxs-lookup"><span data-stu-id="95505-103">How to: Run an Operation in the Background</span></span>
<span data-ttu-id="95505-104">Jeśli masz dużo czasu na ukończenie operacji, która nie ma być przyczyną opóźnień w interfejsie użytkownika, możesz użyć <xref:System.ComponentModel.BackgroundWorker> klasy do uruchomienia operacji w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="95505-104">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="95505-105">Poniższy przykład kodu pokazuje, jak uruchomić czasochłonną operację w tle.</span><span class="sxs-lookup"><span data-stu-id="95505-105">The following code example shows how to run a time-consuming operation in the background.</span></span> <span data-ttu-id="95505-106">Formularz zawiera przyciski **Start** i **Cancel** .</span><span class="sxs-lookup"><span data-stu-id="95505-106">The form has **Start** and **Cancel** buttons.</span></span> <span data-ttu-id="95505-107">Kliknij przycisk **Uruchom** , aby uruchomić operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="95505-107">Click the **Start** button to run an asynchronous operation.</span></span> <span data-ttu-id="95505-108">Kliknij przycisk **Anuluj** , aby zatrzymać uruchomioną operację asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="95505-108">Click the **Cancel** button to stop a running asynchronous operation.</span></span> <span data-ttu-id="95505-109">Wyniki każdej operacji są wyświetlane w <xref:System.Windows.Forms.MessageBox> .</span><span class="sxs-lookup"><span data-stu-id="95505-109">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="95505-110">W programie Visual Studio jest dostępna szeroka pomoc techniczna dla tego zadania.</span><span class="sxs-lookup"><span data-stu-id="95505-110">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="95505-111">Zobacz również [Przewodnik: uruchamianie operacji w tle](walkthrough-running-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="95505-111">Also see [Walkthrough: Running an Operation in the Background](walkthrough-running-an-operation-in-the-background.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95505-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="95505-112">Example</span></span>  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95505-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="95505-113">Compiling the Code</span></span>  
 <span data-ttu-id="95505-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="95505-114">This example requires:</span></span>  
  
- <span data-ttu-id="95505-115">Odwołania do zestawów system, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="95505-115">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95505-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95505-116">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="95505-117">Instrukcje: implementowanie formularza korzystającego z operacji w tle</span><span class="sxs-lookup"><span data-stu-id="95505-117">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="95505-118">BackgroundWorker, składnik</span><span class="sxs-lookup"><span data-stu-id="95505-118">BackgroundWorker Component</span></span>](backgroundworker-component.md)
