---
title: Typ „<typename>” nie jest zdefiniowany
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: c2675d61307d92da1710368668f43af3559060a3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825043"
---
# <a name="type-typename-is-not-defined"></a><span data-ttu-id="25880-102">Typ "\<typename >' nie jest zdefiniowana</span><span class="sxs-lookup"><span data-stu-id="25880-102">Type '\<typename>' is not defined</span></span>
<span data-ttu-id="25880-103">Wykonywanie instrukcji wprowadził odwołanie do typu, który nie został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="25880-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="25880-104">Można zdefiniować typ w instrukcji deklaracji takich jak `Enum`, `Structure`, `Class`, lub `Interface`.</span><span class="sxs-lookup"><span data-stu-id="25880-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="25880-105">**Identyfikator błędu:** BC30002</span><span class="sxs-lookup"><span data-stu-id="25880-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="25880-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="25880-106">To correct this error</span></span>  
  
-   <span data-ttu-id="25880-107">Upewnij się, że w definicji typu i odwołanie, zarówno używają tej samej pisowni.</span><span class="sxs-lookup"><span data-stu-id="25880-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="25880-108">Upewnij się, że definicji typu jest dostępny do odwołania.</span><span class="sxs-lookup"><span data-stu-id="25880-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="25880-109">Na przykład, jeśli typ znajduje się w innym module i został zadeklarowany `Private`, Przenieś definicji typu modułu odwołujący się lub Zadeklaruj go `Public`.</span><span class="sxs-lookup"><span data-stu-id="25880-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="25880-110">Upewnij się, że obszar nazw tego typu nie jest ponownie zdefiniować w obrębie projektu.</span><span class="sxs-lookup"><span data-stu-id="25880-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="25880-111">Jeśli tak jest, należy użyć `Global` — słowo kluczowe pełnej nazwy typu.</span><span class="sxs-lookup"><span data-stu-id="25880-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="25880-112">Na przykład, jeśli projektu definiuje obszar nazw o nazwie `System`, <xref:System.Object?displayProperty=nameWithType> typu nie można uzyskać dostępu, chyba że jest to w pełni kwalifikowaną nazwą zawierającą `Global` — słowo kluczowe: `Global.System.Object`.</span><span class="sxs-lookup"><span data-stu-id="25880-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="25880-113">Jeśli typ jest zdefiniowany, ale obiekt biblioteki lub bibliotekę typów, w którym jest zdefiniowany, nie jest zarejestrowany w Visual Basic, kliknij kolejno pozycje **Dodaj odwołanie** na **projektu** menu, a następnie wybierz odpowiedni obiekt biblioteki lub bibliotekę typów.</span><span class="sxs-lookup"><span data-stu-id="25880-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="25880-114">Upewnij się, że typ w zestawie, który jest częścią profilu docelowej platformy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25880-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="25880-115">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z celem błędy programu .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="25880-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25880-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25880-116">See also</span></span>

- [<span data-ttu-id="25880-117">Przestrzenie nazw w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25880-117">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="25880-118">Enum, instrukcja</span><span class="sxs-lookup"><span data-stu-id="25880-118">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="25880-119">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="25880-119">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="25880-120">Class, instrukcja</span><span class="sxs-lookup"><span data-stu-id="25880-120">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="25880-121">Instrukcja Interface</span><span class="sxs-lookup"><span data-stu-id="25880-121">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="25880-122">Zarządzanie odwołaniami w projekcie</span><span class="sxs-lookup"><span data-stu-id="25880-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
