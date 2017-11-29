---
title: /codepage (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 609373ed0e58eec86a703f33d48d31e27b0b7e3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="codepage-visual-basic"></a>/codepage (Visual Basic)
Określa stronę kodową do użycia dla wszystkich plików kodu źródłowego w kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/codepage:id  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`id`|Wymagany. Kompilator używa strona kodowa określona przez `id` interpretować kodowanie plików źródłowych.|  
  
## <a name="remarks"></a>Uwagi  
 Aby skompilować kod źródłowy został zapisany ze specyficznym kodowaniem, można użyć `/codepage` do określ stronę kodową, która powinna być używana. `/codepage` Opcja ma zastosowanie do wszystkich plików kodu źródłowego w sieci kompilacji. Aby uzyskać więcej informacji, zobacz [kodowania znaków w programie .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).  
  
 `/codepage` Opcja nie jest potrzebna, jeśli pliki kodu źródłowego zostały zapisane przy użyciu bieżącej strony kodowej ANSI, Unicode lub UTF-8 za pomocą podpisu. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]zapisuje wszystkie pliki kodu źródłowego z bieżącej strony kodowej ANSI domyślnie, chyba że użytkownik określi inne kodowanie w **kodowanie** okno dialogowe. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]używa **kodowanie** okno dialogowe, aby otworzyć zapisane przy użyciu innej strony kodowej plików kodu źródłowego.  
  
> [!NOTE]
>  `/codepage` Opcja nie jest dostępne w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] środowisko projektowe; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
