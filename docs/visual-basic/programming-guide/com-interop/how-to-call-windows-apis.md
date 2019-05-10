---
title: 'Instrukcje: Wywoływanie Windows API (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 3769da28e1c9a27c8363b0d6ec639cedaf0f03be
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624856"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="618a9-102">Instrukcje: Wywoływanie Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="618a9-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="618a9-103">W tym przykładzie definiuje i wywołuje `MessageBox` funkcji w bibliotece user32.dll i następnie przekazuje ciąg do niego.</span><span class="sxs-lookup"><span data-stu-id="618a9-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="618a9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="618a9-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="618a9-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="618a9-105">Compiling the Code</span></span>  
 <span data-ttu-id="618a9-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="618a9-106">This example requires:</span></span>  
  
- <span data-ttu-id="618a9-107">Odwołanie do <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="618a9-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="618a9-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="618a9-108">Robust Programming</span></span>  
 <span data-ttu-id="618a9-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="618a9-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="618a9-110">Metoda nie jest statyczna, jest abstrakcyjny lub został wcześniej zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="618a9-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="618a9-111">Typ elementu nadrzędnego jest interfejsem lub długość *nazwa* lub *Nazwa_pliku_dll* wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="618a9-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="618a9-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="618a9-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="618a9-113">*Nazwa* lub *Nazwa_pliku_dll* jest `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="618a9-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="618a9-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="618a9-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="618a9-115">Typ zawierający poprzednio utworzono za pomocą `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="618a9-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="618a9-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="618a9-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="618a9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="618a9-117">See also</span></span>

- [<span data-ttu-id="618a9-118">Im bliżej wywołania platformy</span><span class="sxs-lookup"><span data-stu-id="618a9-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="618a9-119">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="618a9-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="618a9-120">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="618a9-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="618a9-121">[Definiowanie metody przy użyciu odbicia emisji](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="618a9-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="618a9-122">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="618a9-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="618a9-123">Usługa międzyoperacyjna modelu COM</span><span class="sxs-lookup"><span data-stu-id="618a9-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
