---
title: Zabezpieczanie danych o stanie
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
ms.openlocfilehash: c30bd2fe9e1ed371be2db60739d3b329fea788c7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705902"
---
# <a name="securing-state-data"></a><span data-ttu-id="8440f-102">Zabezpieczanie danych o stanie</span><span class="sxs-lookup"><span data-stu-id="8440f-102">Securing State Data</span></span>
<span data-ttu-id="8440f-103">Aplikacje, które obsługują dane poufne lub podejmują jakiekolwiek decyzje dotyczące zabezpieczeń, muszą zachować te dane w ramach własnych kontroli i nie mogą być bezpośrednio dostępne w innym potencjalnie złośliwym kodzie.</span><span class="sxs-lookup"><span data-stu-id="8440f-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="8440f-104">Najlepszym sposobem ochrony danych w pamięci jest zadeklarowanie danych jako prywatnych lub wewnętrznych (z zakresem ograniczonym do tego samego zestawu).</span><span class="sxs-lookup"><span data-stu-id="8440f-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="8440f-105">Jednak nawet te dane podlegają dostępowi, należy pamiętać o:</span><span class="sxs-lookup"><span data-stu-id="8440f-105">However, even this data is subject to access you should be aware of:</span></span>  
  
- <span data-ttu-id="8440f-106">Korzystanie z mechanizmów odbicia, wysoce zaufany kod, który może odwoływać się do obiektu, może pobierać i ustawiać prywatnych członków.</span><span class="sxs-lookup"><span data-stu-id="8440f-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
- <span data-ttu-id="8440f-107">Przy użyciu serializacji wysoce zaufany kod może efektywnie uzyskać i ustawić prywatne składowe, jeśli ma dostęp do odpowiednich danych w serializowanej formie obiektu.</span><span class="sxs-lookup"><span data-stu-id="8440f-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
- <span data-ttu-id="8440f-108">W obszarze Debugowanie można odczytać te dane.</span><span class="sxs-lookup"><span data-stu-id="8440f-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="8440f-109">Upewnij się, że żadna z własnych metod lub właściwości nie ujawnia tych wartości przypadkowo.</span><span class="sxs-lookup"><span data-stu-id="8440f-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8440f-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8440f-110">See also</span></span>

- [<span data-ttu-id="8440f-111">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="8440f-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
