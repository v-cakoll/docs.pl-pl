---
title: 'Instrukcje: Udostępnianie zestawu innym aplikacjom'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b1ef195458dd2de95eeb5e25089339e55d9e3fbb
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972950"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="e4aed-102">Instrukcje: Udostępnianie zestawu innym aplikacjom</span><span class="sxs-lookup"><span data-stu-id="e4aed-102">How to: Share an assembly with other applications</span></span>
<span data-ttu-id="e4aed-103">Zestawy mogą być prywatne lub udostępnione: Domyślnie większość prostych programów składa się z zestawu prywatnego, ponieważ nie są przeznaczone do użytku przez inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="e4aed-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="e4aed-104">W celu udostępnienia zestawu innym aplikacjom należy umieścić je w [globalnej pamięci podręcznej zestawów (GAC)](gac.md).</span><span class="sxs-lookup"><span data-stu-id="e4aed-104">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="e4aed-105">Aby udostępnić zestaw:</span><span class="sxs-lookup"><span data-stu-id="e4aed-105">To share an assembly:</span></span>
  
1. <span data-ttu-id="e4aed-106">Utwórz zestaw.</span><span class="sxs-lookup"><span data-stu-id="e4aed-106">Create your assembly.</span></span> <span data-ttu-id="e4aed-107">Aby uzyskać więcej informacji, zobacz [Tworzenie zestawów](../../standard/assembly/create.md).</span><span class="sxs-lookup"><span data-stu-id="e4aed-107">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="e4aed-108">Przypisz silną nazwę do zestawu.</span><span class="sxs-lookup"><span data-stu-id="e4aed-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="e4aed-109">Aby uzyskać więcej informacji, zobacz [jak: Podpisz zestaw silną nazwą](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="e4aed-109">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="e4aed-110">Przypisz informacje o wersji do Twojego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e4aed-110">Assign version information to your assembly.</span></span> <span data-ttu-id="e4aed-111">Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="e4aed-111">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="e4aed-112">Dodaj swój zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="e4aed-112">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="e4aed-113">Aby uzyskać więcej informacji, zobacz [jak: Zainstaluj zestaw w globalnej pamięci podręcznej](install-assembly-into-gac.md)zestawów.</span><span class="sxs-lookup"><span data-stu-id="e4aed-113">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="e4aed-114">Uzyskaj dostęp do typów zawartych w zestawie z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e4aed-114">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="e4aed-115">Aby uzyskać więcej informacji, zobacz [jak: Odwołuje się do zestawu](../../standard/assembly/reference-strong-named.md)o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="e4aed-115">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4aed-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4aed-116">See also</span></span>

- [<span data-ttu-id="e4aed-117">C#Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="e4aed-117">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="e4aed-118">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4aed-118">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="e4aed-119">Program z zestawami</span><span class="sxs-lookup"><span data-stu-id="e4aed-119">Program with assemblies</span></span>](../../standard/assembly/program.md)
