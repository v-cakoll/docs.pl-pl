---
title: 'Instrukcje: Generowanie zestawów międzyoperacyjnych z bibliotek typów'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a3ee82a9091f0caeee010ec79632ce703efb589
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338842"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="5cd97-102">Instrukcje: Generowanie zestawów międzyoperacyjnych z bibliotek typów</span><span class="sxs-lookup"><span data-stu-id="5cd97-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="5cd97-103">[Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) jest narzędziem wiersza polecenia, który konwertuje klasy coclass i interfejsy zawarte w bibliotece typów modelu COM w metadanych.</span><span class="sxs-lookup"><span data-stu-id="5cd97-103">The [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="5cd97-104">To narzędzie automatycznie tworzy zestaw międzyoperacyjny i przestrzeni nazw, aby uzyskać informacje o typie.</span><span class="sxs-lookup"><span data-stu-id="5cd97-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="5cd97-105">Po udostępnieniu metadanych klas zarządzanych klientów można tworzenia wystąpień tego typu COM i wywołać jego metody tak, jakby był to wystąpienie programu .NET.</span><span class="sxs-lookup"><span data-stu-id="5cd97-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="5cd97-106">Tlbimp.exe konwertuje metadanych całej biblioteki typów na raz i nie można wygenerować informacji o typie dla podzbioru typów zdefiniowanych w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="5cd97-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="5cd97-107">Do generowania zestawu międzyoperacyjnego z biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="5cd97-107">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="5cd97-108">Użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="5cd97-108">Use the following command:</span></span>  
  
     <span data-ttu-id="5cd97-109">**tlbimp** \<*type-library-file*></span><span class="sxs-lookup"><span data-stu-id="5cd97-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="5cd97-110">Dodawanie **/out:** przełącznika tworzy zestaw międzyoperacyjny nazwą zmieniony, takich jak LOANLib.dll.</span><span class="sxs-lookup"><span data-stu-id="5cd97-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="5cd97-111">Zmienianie nazwy zestawu międzyoperacyjnego może pomóc odróżnić go od oryginalnego DLL modelu COM i uniemożliwić problemy, które mogą wystąpić o takich samych nazwach.</span><span class="sxs-lookup"><span data-stu-id="5cd97-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cd97-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="5cd97-112">Example</span></span>  
 <span data-ttu-id="5cd97-113">Następujące polecenie generuje zestaw Loanlib.dll na `Loanlib` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5cd97-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="5cd97-114">Następujące polecenie generuje zestaw międzyoperacyjny nazwą zmienionego (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="5cd97-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cd97-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cd97-115">See also</span></span>

- [<span data-ttu-id="5cd97-116">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="5cd97-116">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="5cd97-117">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5cd97-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
