---
title: 'Instrukcje: Generowanie zestawów międzyoperacyjnych z bibliotek typów'
description: Generuj zestawy międzyoperacyjnych z bibliotek typów. Użyj importera biblioteki typów (Tlbimp.exe), aby skonwertować klasy coclass i interfejsy z biblioteki typów COM na metadane.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
ms.openlocfilehash: 6f54875d6aadb1da18cf25a1bec0a0e451f4a24c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619562"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="abf26-104">Instrukcje: Generowanie zestawów międzyoperacyjnych z bibliotek typów</span><span class="sxs-lookup"><span data-stu-id="abf26-104">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="abf26-105">[Importer biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) to narzędzie wiersza polecenia, które konwertuje klasy coclass i interfejsy zawarte w bibliotece typów modelu COM na metadane.</span><span class="sxs-lookup"><span data-stu-id="abf26-105">The [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="abf26-106">To narzędzie tworzy zestaw międzyoperacyjny i przestrzeń nazw dla informacji o typie automatycznie.</span><span class="sxs-lookup"><span data-stu-id="abf26-106">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="abf26-107">Po udostępnieniu metadanych klasy zarządzani klienci mogą tworzyć wystąpienia typu COM i wywoływać metody, tak jakby były wystąpieniem programu .NET.</span><span class="sxs-lookup"><span data-stu-id="abf26-107">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="abf26-108">Tlbimp.exe konwertuje całą bibliotekę typów na metadane jednocześnie i nie może generować informacji o typie dla podzbioru typów zdefiniowanych w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="abf26-108">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="abf26-109">Aby wygenerować zestaw międzyoperacyjny z biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="abf26-109">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="abf26-110">Użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="abf26-110">Use the following command:</span></span>  
  
     <span data-ttu-id="abf26-111">**Tlbimp**\<*type-library-file*></span><span class="sxs-lookup"><span data-stu-id="abf26-111">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="abf26-112">Dodanie przełącznika **/out:** powoduje utworzenie zestawu międzyoperacyjnego o zmienionej nazwie, takiej jak LOANLib.dll.</span><span class="sxs-lookup"><span data-stu-id="abf26-112">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="abf26-113">Zmiana nazwy zestawu międzyoperacyjnego może pomóc w odróżnieniu od oryginalnej biblioteki DLL modelu COM i zapobiec problemom, które mogą wystąpić w przypadku zduplikowanych nazw.</span><span class="sxs-lookup"><span data-stu-id="abf26-113">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abf26-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="abf26-114">Example</span></span>  
 <span data-ttu-id="abf26-115">Następujące polecenie generuje zestaw Loanlib.dll w `Loanlib` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="abf26-115">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```console  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="abf26-116">Następujące polecenie tworzy zestaw międzyoperacyjny o zmienionej nazwie (LOANLib.dll).</span><span class="sxs-lookup"><span data-stu-id="abf26-116">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```console  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="abf26-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abf26-117">See also</span></span>

- [<span data-ttu-id="abf26-118">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="abf26-118">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="abf26-119">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="abf26-119">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
