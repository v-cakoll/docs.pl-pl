---
title: 'Porady: dzielenie się zestawem z innymi aplikacjami (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 5388aedc-cb42-4622-8b70-8e701eee057a
ms.openlocfilehash: a7f6b49e8389108528c44d7464a2e68149dfa940
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062900"
---
# <a name="how-to-share-an-assembly-with-other-applications-visual-basic"></a><span data-ttu-id="04bd4-102">Porady: dzielenie się zestawem z innymi aplikacjami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04bd4-102">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>
<span data-ttu-id="04bd4-103">Zestawy mogą być prywatne lub udostępnione: domyślnie większości programów proste składają się z zestawu prywatnego, ponieważ nie są przeznaczone do użycia przez inne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="04bd4-103">Assemblies can be private or shared: by default, most simple programs consist of a private assembly because they are not intended to be used by other applications.</span></span>  
  
 <span data-ttu-id="04bd4-104">Aby można było dzielenie się zestawem z innymi aplikacjami, muszą być umieszczone w [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span><span class="sxs-lookup"><span data-stu-id="04bd4-104">In order to share an assembly with other applications, it must be placed in the [Global Assembly Cache](../../../../framework/app-domains/gac.md) (GAC).</span></span>  
  
### <a name="sharing-an-assembly"></a><span data-ttu-id="04bd4-105">Współużytkowanie zestawu</span><span class="sxs-lookup"><span data-stu-id="04bd4-105">Sharing an assembly</span></span>  
  
1.  <span data-ttu-id="04bd4-106">Utwórz zestaw.</span><span class="sxs-lookup"><span data-stu-id="04bd4-106">Create your assembly.</span></span> <span data-ttu-id="04bd4-107">Aby uzyskać więcej informacji, zobacz [tworzenia zestawów](../../../../framework/app-domains/create-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="04bd4-107">For more information, see [Creating Assemblies](../../../../framework/app-domains/create-assemblies.md).</span></span>  
  
2.  <span data-ttu-id="04bd4-108">Do zestawu, należy przypisać silną nazwę.</span><span class="sxs-lookup"><span data-stu-id="04bd4-108">Assign a strong name to your assembly.</span></span> <span data-ttu-id="04bd4-109">Aby uzyskać więcej informacji, zobacz [porady: podpisywanie zestawu za pomocą silnej nazwy](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="04bd4-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
3.  <span data-ttu-id="04bd4-110">Informacje o wersji należy przypisać do swojego zestawu.</span><span class="sxs-lookup"><span data-stu-id="04bd4-110">Assign version information to your assembly.</span></span> <span data-ttu-id="04bd4-111">Aby uzyskać więcej informacji, zobacz [przechowywanie wersji zestawu](../../../../framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="04bd4-111">For more information, see [Assembly Versioning](../../../../framework/app-domains/assembly-versioning.md).</span></span>  
  
4.  <span data-ttu-id="04bd4-112">Dodaj zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="04bd4-112">Add your assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="04bd4-113">Aby uzyskać więcej informacji, zobacz [porady: Instalowanie zestawu w globalnej pamięci podręcznej zestawów](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span><span class="sxs-lookup"><span data-stu-id="04bd4-113">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).</span></span>  
  
5.  <span data-ttu-id="04bd4-114">Dostęp do typów są zawarte w zestawie z innych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="04bd4-114">Access the types contained in the assembly from the other applications.</span></span> <span data-ttu-id="04bd4-115">Aby uzyskać więcej informacji, zobacz [porady: odwołanie do zestawu Strong-Named](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span><span class="sxs-lookup"><span data-stu-id="04bd4-115">For more information, see [How to: Reference a Strong-Named Assembly](https://msdn.microsoft.com/library/4c6a406a-b5eb-44fa-b4ed-4e95bb95a813).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04bd4-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04bd4-116">See Also</span></span>  
 <span data-ttu-id="04bd4-117">[Pojęcia związane z programowaniem](../../../../visual-basic/programming-guide/concepts/index.md) [zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span><span class="sxs-lookup"><span data-stu-id="04bd4-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)</span></span>  
 [<span data-ttu-id="04bd4-118">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="04bd4-118">Programming with Assemblies</span></span>](../../../../framework/app-domains/programming-with-assemblies.md)
