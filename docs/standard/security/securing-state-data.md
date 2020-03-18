---
title: Zabezpieczanie danych o stanie
description: Deklaruj dane stanu jako zmienne prywatne lub wewnętrzne, aby ograniczyć dostęp do nich. Takie dane są nadal dostępne za pomocą odbicia, serializacji i debugowania.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: f95bf409f7eef8c2636d3c180d2bbd95fbc689c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186823"
---
# <a name="securing-state-data"></a><span data-ttu-id="c3c4b-104">Zabezpieczanie danych o stanie</span><span class="sxs-lookup"><span data-stu-id="c3c4b-104">Securing State Data</span></span>
<span data-ttu-id="c3c4b-105">Aplikacje, które obsługują poufne dane lub podejmują wszelkiego rodzaju decyzje dotyczące zabezpieczeń, muszą zachować te dane pod własną kontrolą i nie mogą zezwolić innemu potencjalnie złośliwemu kodowi na bezpośredni dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="c3c4b-105">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="c3c4b-106">Najlepszym sposobem ochrony danych w pamięci jest zadeklarowanie danych jako zmiennych prywatnych lub wewnętrznych (z zakresem ograniczonym do tego samego zestawu).</span><span class="sxs-lookup"><span data-stu-id="c3c4b-106">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="c3c4b-107">Jednak nawet te dane podlegają dostępowi, o którym powinieneś wiedzieć:</span><span class="sxs-lookup"><span data-stu-id="c3c4b-107">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="c3c4b-108">Za pomocą mechanizmów odbicia, wysoce zaufany kod, który może odwoływać się do obiektu można uzyskać i ustawić członków prywatnych.</span><span class="sxs-lookup"><span data-stu-id="c3c4b-108">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="c3c4b-109">Za pomocą serializacji, wysoce zaufany kod można skutecznie uzyskać i ustawić członków prywatnych, jeśli można uzyskać dostęp do odpowiednich danych w postaci serializowane obiektu.</span><span class="sxs-lookup"><span data-stu-id="c3c4b-109">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="c3c4b-110">W obszarze debugowania te dane mogą być odczytywane.</span><span class="sxs-lookup"><span data-stu-id="c3c4b-110">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="c3c4b-111">Upewnij się, że żadna z własnych metod lub właściwości nie udostępnia tych wartości przypadkowo.</span><span class="sxs-lookup"><span data-stu-id="c3c4b-111">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3c4b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3c4b-112">See also</span></span>

- [<span data-ttu-id="c3c4b-113">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="c3c4b-113">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
