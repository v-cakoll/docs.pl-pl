---
title: 'Instrukcje: udostępnianie zestawu innym aplikacjom'
description: Zobacz, jak udostępnić zestaw innym aplikacjom w programie .NET. Zestawy mogą być prywatne (domyślne) lub udostępnione. Aby udostępnić zestaw, umieść go w pamięci podręcznej GAC.
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 9cef25059968875f17ce5dc77b04c44a2f3945f6
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104651"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="2bf25-105">Instrukcje: udostępnianie zestawu innym aplikacjom</span><span class="sxs-lookup"><span data-stu-id="2bf25-105">How to: Share an assembly with other applications</span></span>
<span data-ttu-id="2bf25-106">Zestawy mogą być prywatne lub udostępnione: Domyślnie większość prostych programów składa się z zestawu prywatnego, ponieważ nie są przeznaczone do użytku przez inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="2bf25-106">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="2bf25-107">W celu udostępnienia zestawu innym aplikacjom należy umieścić je w [globalnej pamięci podręcznej zestawów (GAC)](gac.md).</span><span class="sxs-lookup"><span data-stu-id="2bf25-107">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="2bf25-108">Aby udostępnić zestaw:</span><span class="sxs-lookup"><span data-stu-id="2bf25-108">To share an assembly:</span></span>
  
1. <span data-ttu-id="2bf25-109">Utwórz zestaw.</span><span class="sxs-lookup"><span data-stu-id="2bf25-109">Create your assembly.</span></span> <span data-ttu-id="2bf25-110">Aby uzyskać więcej informacji, zobacz [Tworzenie zestawów](../../standard/assembly/create.md).</span><span class="sxs-lookup"><span data-stu-id="2bf25-110">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="2bf25-111">Przypisz silną nazwę do zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bf25-111">Assign a strong name to your assembly.</span></span> <span data-ttu-id="2bf25-112">Aby uzyskać więcej informacji, zobacz [jak: podpisywanie zestawu za pomocą silnej nazwy](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="2bf25-112">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="2bf25-113">Przypisz informacje o wersji do Twojego zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bf25-113">Assign version information to your assembly.</span></span> <span data-ttu-id="2bf25-114">Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="2bf25-114">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="2bf25-115">Dodaj swój zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="2bf25-115">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="2bf25-116">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="2bf25-116">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="2bf25-117">Uzyskaj dostęp do typów zawartych w zestawie z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2bf25-117">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="2bf25-118">Aby uzyskać więcej informacji, zobacz [jak: odwołanie do zestawu o silnej nazwie](../../standard/assembly/reference-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="2bf25-118">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf25-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bf25-119">See also</span></span>

- [<span data-ttu-id="2bf25-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2bf25-120">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="2bf25-121">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2bf25-121">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="2bf25-122">Programowanie przy użyciu zestawów</span><span class="sxs-lookup"><span data-stu-id="2bf25-122">Program with assemblies</span></span>](../../standard/assembly/index.md)
