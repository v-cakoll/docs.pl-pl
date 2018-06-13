---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 383b6adae94c27efdd236de31ddfa8d16a6d4648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648531"
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
|`id`|Wymagana. Kompilator używa strona kodowa określona przez `id` interpretować kodowanie plików źródłowych.|  
  
## <a name="remarks"></a>Uwagi  
 Aby skompilować kod źródłowy został zapisany ze specyficznym kodowaniem, można użyć `-codepage` do określ stronę kodową, która powinna być używana. `-codepage` Opcja ma zastosowanie do wszystkich plików kodu źródłowego w sieci kompilacji. Aby uzyskać więcej informacji, zobacz [kodowania znaków w programie .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).  
  
 `-codepage` Opcja nie jest potrzebna, jeśli pliki kodu źródłowego zostały zapisane przy użyciu bieżącej strony kodowej ANSI, Unicode lub UTF-8 za pomocą podpisu. Visual Studio zapisuje wszystkie pliki kodu źródłowego z bieżącej strony kodowej ANSI domyślnie, chyba że użytkownik określi inne kodowanie w **kodowanie** okno dialogowe. Visual Studio będzie korzystać **kodowanie** okno dialogowe, aby otworzyć zapisane przy użyciu innej strony kodowej plików kodu źródłowego.  
  
> [!NOTE]
>  `-codepage` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
