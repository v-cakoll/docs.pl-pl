---
title: Współdziałanie COM w aplikacjach .NET Framework (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: ceef4255321e208911a16db0227890bc6654b8c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642927"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a><span data-ttu-id="0491c-102">Współdziałanie COM w aplikacjach .NET Framework (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0491c-102">COM Interoperability in .NET Framework Applications (Visual Basic)</span></span>
<span data-ttu-id="0491c-103">Jeśli chcesz użyć obiekty COM i .NET Framework w tej samej aplikacji, należy spełnić różnice w jaki sposób obiekty istnieją w pamięci.</span><span class="sxs-lookup"><span data-stu-id="0491c-103">When you want to use COM objects and .NET Framework objects in the same application, you need to address the differences in how the objects exist in memory.</span></span> <span data-ttu-id="0491c-104">Obiekt .NET Framework znajduje się w pamięci zarządzanej — pamięci kontrolowane przez środowisko uruchomieniowe języka wspólnego — i mogą być przenoszone w czasie wykonywania, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="0491c-104">A .NET Framework object is located in managed memory—the memory controlled by the common language runtime—and may be moved by the runtime as needed.</span></span> <span data-ttu-id="0491c-105">Obiekt COM znajduje się w pamięci niezarządzanej i przenieść do innej lokalizacji pamięci nie jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="0491c-105">A COM object is located in unmanaged memory and is not expected to move to another memory location.</span></span> <span data-ttu-id="0491c-106">Visual Studio i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] narzędzia do sterowania interakcji z tych zarządzanych i niezarządzanych składników.</span><span class="sxs-lookup"><span data-stu-id="0491c-106">Visual Studio and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide tools to control the interaction of these managed and unmanaged components.</span></span> <span data-ttu-id="0491c-107">Aby uzyskać więcej informacji na temat kodu zarządzanego, zobacz [środowisko uruchomieniowe języka wspólnego](../../../standard/clr.md).</span><span class="sxs-lookup"><span data-stu-id="0491c-107">For more information about managed code, see [Common Language Runtime](../../../standard/clr.md).</span></span>  
  
 <span data-ttu-id="0491c-108">Oprócz przy użyciu obiektów COM w aplikacjach .NET, ma może używać języka Visual Basic umożliwiające tworzenie obiektów dostępny z kodem niezarządzanym za pośrednictwem modelu COM.</span><span class="sxs-lookup"><span data-stu-id="0491c-108">In addition to using COM objects in .NET applications, you may also want to use Visual Basic to develop objects accessible from unmanaged code through COM.</span></span>  
  
 <span data-ttu-id="0491c-109">Linki na tej stronie zawierają szczegółowe informacje o interakcjach między obiektami COM i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0491c-109">The links on this page provide details on the interactions between COM and .NET Framework objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0491c-110">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0491c-110">Related Sections</span></span>  
 [<span data-ttu-id="0491c-111">Usługa międzyoperacyjna modelu COM</span><span class="sxs-lookup"><span data-stu-id="0491c-111">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 <span data-ttu-id="0491c-112">Zawiera łącza do tematów obejmujących współdziałanie COM w języku Visual Basic, w tym modelu COM obiektów, ActiveX formantów, biblioteki DLL systemu Win32, zarządzanych obiektów i dziedziczenia z obiektami COM.</span><span class="sxs-lookup"><span data-stu-id="0491c-112">Provides links to topics covering COM interoperability in Visual Basic, including COM objects, ActiveX controls, Win32 DLLs, managed objects, and inheritance of COM objects.</span></span>  
  
 [<span data-ttu-id="0491c-113">COM Interop Wrapper — błąd</span><span class="sxs-lookup"><span data-stu-id="0491c-113">COM Interop Wrapper Error</span></span>](/cpp/misc/com-interop-wrapper-error)  
 <span data-ttu-id="0491c-114">Opisuje skutki i opcje, czy system projektu nie może utworzyć otoka współdziałania COM dla poszczególnych składników.</span><span class="sxs-lookup"><span data-stu-id="0491c-114">Describes the consequences and options if the project system cannot create a COM interoperability wrapper for a particular component.</span></span>  
  
 [<span data-ttu-id="0491c-115">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="0491c-115">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="0491c-116">Krótko opisano niektóre problemy interakcji między zarządzanymi i niezarządzanymi kodu i linki do dalszych badań.</span><span class="sxs-lookup"><span data-stu-id="0491c-116">Briefly describes some of the interaction issues between managed and unmanaged code, and provides links for further study.</span></span>  
  
 [<span data-ttu-id="0491c-117">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="0491c-117">COM Wrappers</span></span>](../../../framework/interop/com-wrappers.md)  
 <span data-ttu-id="0491c-118">W tym artykule omówiono wywoływane otoki środowiska uruchomieniowego, które umożliwiają kodu zarządzanego do wywołania metody modelu COM, i wywoływane otoki COM, które umożliwiają klientom COM wywoływanie metody obiektu .NET.</span><span class="sxs-lookup"><span data-stu-id="0491c-118">Discusses runtime callable wrappers, which allow managed code to call COM methods, and COM callable wrappers, which allow COM clients to call .NET object methods.</span></span>  
  
 [<span data-ttu-id="0491c-119">Współdziałanie COM zaawansowane</span><span class="sxs-lookup"><span data-stu-id="0491c-119">Advanced COM Interoperability</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="0491c-120">Zawiera łącza do tematów obejmujących współdziałanie COM względem otoki, wyjątki dziedziczenia, wątki, zdarzenia, konwersje i organizowanie.</span><span class="sxs-lookup"><span data-stu-id="0491c-120">Provides links to topics covering COM interoperability with respect to wrappers, exceptions, inheritance, threading, events, conversions, and marshaling.</span></span>  
  
 [<span data-ttu-id="0491c-121">Tlbimp.exe (importer biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="0491c-121">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 <span data-ttu-id="0491c-122">W tym artykule omówiono narzędzie, które umożliwia konwertowanie definicji typu znaleziony w Biblioteka typów COM na równoważne definicje w zestawie środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="0491c-122">Discusses the tool you can use to convert the type definitions found within a COM type library into equivalent definitions in a common language runtime assembly.</span></span>
