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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe941fff7091fb579e41a3c417dbb2129bcf3e8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580786"
---
# <a name="securing-state-data"></a><span data-ttu-id="00a6c-102">Zabezpieczanie danych o stanie</span><span class="sxs-lookup"><span data-stu-id="00a6c-102">Securing State Data</span></span>
<span data-ttu-id="00a6c-103">Aplikacji, które obsługują dane poufne lub wprowadzić dowolny rodzaj decyzje zabezpieczeń muszą zachować te dane pod kontrolą własne i nie może dopuścić do innych potencjalnie niebezpiecznego kodu bezpośrednio uzyskać dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="00a6c-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="00a6c-104">Najlepszym sposobem na potrzeby ochrony danych w pamięci jest deklaruje dane jako prywatny lub wewnętrzny (z zakresem, ograniczone do tego samego zestawu) zmienne.</span><span class="sxs-lookup"><span data-stu-id="00a6c-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="00a6c-105">Jednak nawet te dane podlega dostępu, które należy zwrócić uwagę:</span><span class="sxs-lookup"><span data-stu-id="00a6c-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="00a6c-106">Za pomocą mechanizmów odbicia, wysoce zaufanych kod, który może odwoływać się do obiektu można get i set prywatne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="00a6c-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="00a6c-107">Za pomocą serializacji, wysoce zaufanych kodu można skutecznie get i set prywatne elementy członkowskie Jeśli można uzyskać dostępu do odpowiednich danych w formularzu serializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="00a6c-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="00a6c-108">W obszarze debugowania, mogą być odczytywane dane.</span><span class="sxs-lookup"><span data-stu-id="00a6c-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="00a6c-109">Upewnij się, że żaden z własnych metody lub właściwości przypadkowo udostępnia te wartości.</span><span class="sxs-lookup"><span data-stu-id="00a6c-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00a6c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00a6c-110">See Also</span></span>  
 [<span data-ttu-id="00a6c-111">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="00a6c-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
