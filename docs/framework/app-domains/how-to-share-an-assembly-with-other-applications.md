---
title: 'Instrukcje: udostępnianie zestawu innym aplikacjom'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b4c183c3fc0b04121be8bbc2db4027887cbc3132
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644290"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a><span data-ttu-id="b14b5-102">Instrukcje: udostępnianie zestawu innym aplikacjom</span><span class="sxs-lookup"><span data-stu-id="b14b5-102">How to: Share an assembly with other applications</span></span>
<span data-ttu-id="b14b5-103">Zestawy mogą być prywatne lub udostępnione: Domyślnie większość prostych programów składa się z zestawu prywatnego, ponieważ nie są przeznaczone do użytku przez inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="b14b5-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  

<span data-ttu-id="b14b5-104">W celu udostępnienia zestawu innym aplikacjom należy umieścić je w [globalnej pamięci podręcznej zestawów (GAC)](gac.md).</span><span class="sxs-lookup"><span data-stu-id="b14b5-104">In order to share an assembly with other applications, it must be placed in the [global assembly cache (GAC)](gac.md).</span></span>  
  
<span data-ttu-id="b14b5-105">Aby udostępnić zestaw:</span><span class="sxs-lookup"><span data-stu-id="b14b5-105">To share an assembly:</span></span>
  
1. <span data-ttu-id="b14b5-106">Utwórz zestaw.</span><span class="sxs-lookup"><span data-stu-id="b14b5-106">Create your assembly.</span></span> <span data-ttu-id="b14b5-107">Aby uzyskać więcej informacji, zobacz [Tworzenie zestawów](../../standard/assembly/create.md).</span><span class="sxs-lookup"><span data-stu-id="b14b5-107">For more information, see [Create assemblies](../../standard/assembly/create.md).</span></span>  
  
2. <span data-ttu-id="b14b5-108">Przypisz silną nazwę do zestawu.</span><span class="sxs-lookup"><span data-stu-id="b14b5-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="b14b5-109">Aby uzyskać więcej informacji, zobacz [jak: podpisywanie zestawu za pomocą silnej nazwy](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="b14b5-109">For more information, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>  
  
3. <span data-ttu-id="b14b5-110">Przypisz informacje o wersji do Twojego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b14b5-110">Assign version information to your assembly.</span></span> <span data-ttu-id="b14b5-111">Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="b14b5-111">For more information, see [Assembly versioning](../../standard/assembly/versioning.md).</span></span>  
  
4. <span data-ttu-id="b14b5-112">Dodaj swój zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="b14b5-112">Add your assembly to the global assembly cache.</span></span> <span data-ttu-id="b14b5-113">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](install-assembly-into-gac.md).</span><span class="sxs-lookup"><span data-stu-id="b14b5-113">For more information, see [How to: Install an assembly into the global assembly cache](install-assembly-into-gac.md).</span></span>  
  
5. <span data-ttu-id="b14b5-114">Uzyskaj dostęp do typów zawartych w zestawie z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b14b5-114">Access the types contained in the assembly from other applications.</span></span> <span data-ttu-id="b14b5-115">Aby uzyskać więcej informacji, zobacz [jak: odwołanie do zestawu o silnej nazwie](../../standard/assembly/reference-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="b14b5-115">For more information, see [How to: Reference a strong-named assembly](../../standard/assembly/reference-strong-named.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b14b5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b14b5-116">See also</span></span>

- [<span data-ttu-id="b14b5-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b14b5-117">C# programming guide</span></span>](../../../api/index.md)
- [<span data-ttu-id="b14b5-118">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b14b5-118">Programming concepts (Visual Basic)</span></span>](../../../api/index.md)
- [<span data-ttu-id="b14b5-119">Programowanie przy użyciu zestawów</span><span class="sxs-lookup"><span data-stu-id="b14b5-119">Program with assemblies</span></span>](../../standard/assembly/index.md)
