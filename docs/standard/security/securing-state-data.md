---
title: Zabezpieczanie danych o stanie
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bd41f5174f426e723ea7e069eaee8f2d367625a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="securing-state-data"></a><span data-ttu-id="21bb3-102">Zabezpieczanie danych o stanie</span><span class="sxs-lookup"><span data-stu-id="21bb3-102">Securing State Data</span></span>
<span data-ttu-id="21bb3-103">Aplikacji, które obsługują dane poufne lub wprowadzić dowolny rodzaj decyzje zabezpieczeń muszą zachować te dane pod kontrolą własne i nie może dopuścić do innych potencjalnie niebezpiecznego kodu bezpośrednio uzyskać dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="21bb3-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="21bb3-104">Najlepszym sposobem na potrzeby ochrony danych w pamięci jest deklaruje dane jako prywatny lub wewnętrzny (z zakresem, ograniczone do tego samego zestawu) zmienne.</span><span class="sxs-lookup"><span data-stu-id="21bb3-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="21bb3-105">Jednak nawet te dane podlega dostępu, które należy zwrócić uwagę:</span><span class="sxs-lookup"><span data-stu-id="21bb3-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="21bb3-106">Za pomocą mechanizmów odbicia, wysoce zaufanych kod, który może odwoływać się do obiektu można get i set prywatne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="21bb3-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="21bb3-107">Za pomocą serializacji, wysoce zaufanych kodu można skutecznie get i set prywatne elementy członkowskie Jeśli można uzyskać dostępu do odpowiednich danych w formularzu serializacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="21bb3-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="21bb3-108">W obszarze debugowania, mogą być odczytywane dane.</span><span class="sxs-lookup"><span data-stu-id="21bb3-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="21bb3-109">Upewnij się, że żaden z własnych metody lub właściwości przypadkowo udostępnia te wartości.</span><span class="sxs-lookup"><span data-stu-id="21bb3-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21bb3-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21bb3-110">See Also</span></span>  
 [<span data-ttu-id="21bb3-111">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="21bb3-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
