---
title: "Zbyt wielu klientów aplikacji DLL"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID47
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b9278134e937ac8bf4626237954432d727ac0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="too-many-dll-application-clients"></a>Zbyt wielu klientów aplikacji DLL
Biblioteki dołączanej (dynamicznie DLL) dla [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] może obsłużyć tylko dostępu przy ograniczonej liczby aplikacji hosta. Aplikacja i inne aplikacje, które są [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] hostów (niektóre z nich mogą być używane przez aplikację) są próby uzyskania dostępu do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] biblioteki DLL w tym samym czasie.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmniejsz liczbę otwartych aplikacji dostęp do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 [Error — typy](../../visual-basic/programming-guide/language-features/error-types.md)
