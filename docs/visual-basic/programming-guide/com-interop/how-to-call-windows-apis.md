---
title: 'Porady: wywoływanie Windows API (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 739516e86917ac24a81cd6387af5576c512ecbc2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515920"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="3ed47-102">Porady: wywoływanie Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ed47-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="3ed47-103">W tym przykładzie definiuje i wywołuje `MessageBox` funkcji w bibliotece user32.dll i następnie przekazuje ciąg do niego.</span><span class="sxs-lookup"><span data-stu-id="3ed47-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ed47-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ed47-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3ed47-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="3ed47-105">Compiling the Code</span></span>  
 <span data-ttu-id="3ed47-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="3ed47-106">This example requires:</span></span>  
  
-   <span data-ttu-id="3ed47-107">Odwołanie do <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3ed47-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3ed47-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="3ed47-108">Robust Programming</span></span>  
 <span data-ttu-id="3ed47-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="3ed47-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="3ed47-110">Metoda nie jest statyczna, jest abstrakcyjny lub został wcześniej zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="3ed47-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="3ed47-111">Typ elementu nadrzędnego jest interfejsem lub długość *nazwa* lub *Nazwa_pliku_dll* wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="3ed47-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="3ed47-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="3ed47-112">(<xref:System.ArgumentException>)</span></span>  
  
-   <span data-ttu-id="3ed47-113">*Nazwa* lub *Nazwa_pliku_dll* jest `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="3ed47-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="3ed47-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="3ed47-114">(<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="3ed47-115">Typ zawierający poprzednio utworzono za pomocą `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="3ed47-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="3ed47-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="3ed47-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed47-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ed47-117">See Also</span></span>  
 [<span data-ttu-id="3ed47-118">Im bliżej wywołania platformy</span><span class="sxs-lookup"><span data-stu-id="3ed47-118">A Closer Look at Platform Invoke</span></span>](https://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [<span data-ttu-id="3ed47-119">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="3ed47-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="3ed47-120">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="3ed47-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="3ed47-121">Definiowanie metody przy użyciu odbicia emisji</span><span class="sxs-lookup"><span data-stu-id="3ed47-121">Defining a Method with Reflection Emit</span></span>](https://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [<span data-ttu-id="3ed47-122">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3ed47-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="3ed47-123">Usługa międzyoperacyjna modelu COM</span><span class="sxs-lookup"><span data-stu-id="3ed47-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
