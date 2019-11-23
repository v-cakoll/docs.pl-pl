---
title: 'Porady: wywoływanie Windows API'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 6f3c53243d7aeb73be81796d5ca185c3a3c41c72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348702"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="98ed3-102">Porady: wywoływanie Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98ed3-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="98ed3-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span><span class="sxs-lookup"><span data-stu-id="98ed3-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98ed3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="98ed3-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98ed3-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="98ed3-105">Compiling the Code</span></span>  
 <span data-ttu-id="98ed3-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="98ed3-106">This example requires:</span></span>  
  
- <span data-ttu-id="98ed3-107">A reference to the <xref:System> namespace.</span><span class="sxs-lookup"><span data-stu-id="98ed3-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="98ed3-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="98ed3-108">Robust Programming</span></span>  
 <span data-ttu-id="98ed3-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="98ed3-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="98ed3-110">The method is not static, is abstract, or has been previously defined.</span><span class="sxs-lookup"><span data-stu-id="98ed3-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="98ed3-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span><span class="sxs-lookup"><span data-stu-id="98ed3-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="98ed3-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="98ed3-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="98ed3-113">The *name* or *dllName* is `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="98ed3-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="98ed3-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="98ed3-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="98ed3-115">The containing type has been previously created using `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="98ed3-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="98ed3-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="98ed3-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ed3-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98ed3-117">See also</span></span>

- [<span data-ttu-id="98ed3-118">A Closer Look at Platform Invoke</span><span class="sxs-lookup"><span data-stu-id="98ed3-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="98ed3-119">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="98ed3-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="98ed3-120">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="98ed3-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="98ed3-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="98ed3-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="98ed3-122">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="98ed3-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="98ed3-123">Usługa międzyoperacyjna modelu COM</span><span class="sxs-lookup"><span data-stu-id="98ed3-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
