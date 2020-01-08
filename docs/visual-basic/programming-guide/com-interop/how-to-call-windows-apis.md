---
title: 'Porady: wywoływanie Windows API'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 9de9f0fbcca291af0b6aadfd8e3fe7033708fbc6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347532"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="b1cb7-102">Porady: wywoływanie Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1cb7-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="b1cb7-103">Ten przykład definiuje i wywołuje funkcję `MessageBox` w User32. dll, a następnie przekazuje do niej ciąg.</span><span class="sxs-lookup"><span data-stu-id="b1cb7-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1cb7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1cb7-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="b1cb7-105">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="b1cb7-105">Compile the code</span></span>  
 <span data-ttu-id="b1cb7-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="b1cb7-106">This example requires:</span></span>  
  
- <span data-ttu-id="b1cb7-107">Odwołanie do przestrzeni nazw <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="b1cb7-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b1cb7-108">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="b1cb7-108">Robust Programming</span></span>  
 <span data-ttu-id="b1cb7-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="b1cb7-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b1cb7-110">Metoda nie jest statyczna, jest abstrakcyjna lub została wcześniej zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="b1cb7-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="b1cb7-111">Typ nadrzędny jest interfejsem lub długość *nazwy* lub *nazwa_pliku_dll* ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="b1cb7-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="b1cb7-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="b1cb7-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="b1cb7-113">*Nazwa* lub *nazwa_pliku_dll* jest `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b1cb7-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="b1cb7-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="b1cb7-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="b1cb7-115">Typ zawierający został wcześniej utworzony przy użyciu `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="b1cb7-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="b1cb7-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="b1cb7-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1cb7-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1cb7-117">See also</span></span>

- [<span data-ttu-id="b1cb7-118">Bliższe spojrzenie na wywołanie platformy</span><span class="sxs-lookup"><span data-stu-id="b1cb7-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="b1cb7-119">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="b1cb7-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="b1cb7-120">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="b1cb7-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="b1cb7-121">[Definiowanie metody przy użyciu emisji odbicia](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b1cb7-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="b1cb7-122">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b1cb7-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="b1cb7-123">Usługa międzyoperacyjna modelu COM</span><span class="sxs-lookup"><span data-stu-id="b1cb7-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
