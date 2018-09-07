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
ms.openlocfilehash: 3c821177ca897e617885425217ac0b6659b5ea6e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44062576"
---
# <a name="securing-state-data"></a><span data-ttu-id="df080-102">Zabezpieczanie danych o stanie</span><span class="sxs-lookup"><span data-stu-id="df080-102">Securing State Data</span></span>
<span data-ttu-id="df080-103">Aplikacje, które obsługują dane poufne lub wprowadzić dowolnego rodzaju decyzje dotyczące bezpieczeństwa należy zachować te dane w ich własnych kontrolą i nie może dopuścić do innego potencjalnie złośliwego kodu bezpośrednio dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="df080-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="df080-104">Najlepszym sposobem, aby chronić dane w pamięci jest do deklarowania dane jako prywatny lub wewnętrzny (z zakresu ograniczone do tego samego zestawu) zmienne.</span><span class="sxs-lookup"><span data-stu-id="df080-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="df080-105">Jednak nawet w tych danych podlega dostępu, których należy wiedzieć:</span><span class="sxs-lookup"><span data-stu-id="df080-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="df080-106">Za pomocą mechanizmów odbicia, wysoce zaufanym kodem, który może odwoływać się do obiektu może pobierać i ustawiać prywatnych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="df080-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="df080-107">Za pomocą serializacji, wysoce zaufanym kodem może efektywnie pobierać i ustawiać prywatne składowe jeśli mogą uzyskać dostępu do odpowiednich danych w postaci serializowanej obiektu.</span><span class="sxs-lookup"><span data-stu-id="df080-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="df080-108">W obszarze debugowania, te dane mogą być odczytywane.</span><span class="sxs-lookup"><span data-stu-id="df080-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="df080-109">Upewnij się, brak swoje własne metody lub właściwości przypadkowo udostępnia te wartości.</span><span class="sxs-lookup"><span data-stu-id="df080-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df080-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df080-110">See also</span></span>

- [<span data-ttu-id="df080-111">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="df080-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
