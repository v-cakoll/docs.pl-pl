---
title: 'Instrukcje: Wywoływanie interfejsów API systemu Windows'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 2c3bb599b79575180eb2b0ec89453f01901f94c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396846"
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="e3f48-102">Porady: wywoływanie Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3f48-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="e3f48-103">Ten przykład definiuje i wywołuje `MessageBox` funkcję w User32. dll, a następnie przekazuje do niej ciąg.</span><span class="sxs-lookup"><span data-stu-id="e3f48-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3f48-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3f48-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="e3f48-105">Kompiluj kod</span><span class="sxs-lookup"><span data-stu-id="e3f48-105">Compile the code</span></span>  
 <span data-ttu-id="e3f48-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e3f48-106">This example requires:</span></span>  
  
- <span data-ttu-id="e3f48-107">Odwołanie do <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e3f48-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e3f48-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="e3f48-108">Robust Programming</span></span>  
 <span data-ttu-id="e3f48-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="e3f48-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="e3f48-110">Metoda nie jest statyczna, jest abstrakcyjna lub została wcześniej zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="e3f48-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="e3f48-111">Typ nadrzędny jest interfejsem lub długość *nazwy* lub *nazwa_pliku_dll* ma wartość zero.</span><span class="sxs-lookup"><span data-stu-id="e3f48-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="e3f48-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="e3f48-112">(<xref:System.ArgumentException>)</span></span>  
  
- <span data-ttu-id="e3f48-113">*Nazwa* lub *nazwa_pliku_dll* ma wartość `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="e3f48-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="e3f48-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="e3f48-114">(<xref:System.ArgumentNullException>)</span></span>  
  
- <span data-ttu-id="e3f48-115">Typ zawierający został wcześniej utworzony przy użyciu `CreateType` .</span><span class="sxs-lookup"><span data-stu-id="e3f48-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="e3f48-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="e3f48-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3f48-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3f48-117">See also</span></span>

- [<span data-ttu-id="e3f48-118">Bliższe spojrzenie na wywołanie platformy</span><span class="sxs-lookup"><span data-stu-id="e3f48-118">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="e3f48-119">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="e3f48-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)
- [<span data-ttu-id="e3f48-120">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="e3f48-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- <span data-ttu-id="e3f48-121">[Definiowanie metody przy użyciu emisji odbicia](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e3f48-121">[Defining a Method with Reflection Emit](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))</span></span>
- [<span data-ttu-id="e3f48-122">Przewodnik: Wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e3f48-122">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
- [<span data-ttu-id="e3f48-123">Międzyoperacyjność modelu COM</span><span class="sxs-lookup"><span data-stu-id="e3f48-123">COM Interop</span></span>](index.md)
