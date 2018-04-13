---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 736b35f51657aa7b21a6a077d70f5e9ff0d4fb85
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
Określa stronę kodową do użycia dla wszystkich plików kodu źródłowego w kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`id`|Wymagany. Kompilator używa strona kodowa określona przez `id` interpretować kodowanie plików źródłowych.|  
  
## <a name="remarks"></a>Uwagi  
 Aby skompilować kod źródłowy został zapisany ze specyficznym kodowaniem, można użyć `-codepage` do określ stronę kodową, która powinna być używana. `-codepage` Opcja ma zastosowanie do wszystkich plików kodu źródłowego w sieci kompilacji. Aby uzyskać więcej informacji, zobacz [kodowania znaków w programie .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).  
  
 `-codepage` Opcja nie jest potrzebna, jeśli pliki kodu źródłowego zostały zapisane przy użyciu bieżącej strony kodowej ANSI, Unicode lub UTF-8 za pomocą podpisu. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] zapisuje wszystkie pliki kodu źródłowego z bieżącej strony kodowej ANSI domyślnie, chyba że użytkownik określi inne kodowanie w **kodowanie** okno dialogowe. [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] używa **kodowanie** okno dialogowe, aby otworzyć zapisane przy użyciu innej strony kodowej plików kodu źródłowego.  
  
> [!NOTE]
>  `-codepage` Opcja nie jest dostępne w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] środowisko projektowe; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
