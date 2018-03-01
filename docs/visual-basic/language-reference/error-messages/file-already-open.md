---
title: "Plik jest już otwarty"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a>Plik jest już otwarty
Czasami pliku muszą zostać zamknięte przed inne `FileOpen` lub można wykonać innych operacji. Wśród możliwych przyczyn tego błędu są:  
  
-   Tryb sekwencyjnych dane wyjściowe `FileOpen` operacja została wykonana dla pliku, który jest już otwarty  
  
-   Oświadczenie odnosi się do otwartego pliku.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Zamknij plik przed wykonaniem instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
