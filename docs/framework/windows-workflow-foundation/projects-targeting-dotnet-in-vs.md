---
title: Zapisywanie w projektach przeznaczonych dla programu .NET Framework 3.0 i 3.5 w programie Visual Studio 2010
ms.date: 03/30/2017
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
ms.openlocfilehash: 1469ce2906c1101bae4098cbcabd4a10a64c1c7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513830"
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a>Zapisywanie w projektach przeznaczonych dla programu .NET Framework 3.0 i 3.5 w programie Visual Studio 2010
Można użyć [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] do tworzenia projektów przeznaczonych [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] w wersji 3.0 lub 3.5. W tym temacie opisano, jak to zrobić.  
  
> [!NOTE]
>  Podczas dodawania działań, upewnij się, że żądanej wersji [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] jest ustawiona. Zmiana wersji docelowej przepływu pracy, po dodaniu działania spowoduje niepowodzenie sprawdzania poprawności przepływu pracy.  
  
> [!WARNING]
>  Otwieranie istniejących przepływów pracy w [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] zawierających .net Framework 3.5 działania spowoduje, że wystąpił błąd w `this.SetValue()`. Aby można było otworzyć projektów utworzonych w poprzednich wersjach programu .net Framework, najpierw otwórz pusty przepływu pracy w Projektancie i Dodaj .net Framework 3.5 działania.  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a>Aby utworzyć środowiska .NET Framework 3.0 lub 3.5 projektu za pomocą programu Visual Studio 2010  
  
1.  Otwórz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Wybierz **pliku**, **nowe**, **projektu**.  
  
3.  Na liście rozwijanej w górnej części okna dialogowego wybierz żądaną wersję [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a>Aby uaktualnić wersję docelową programu .NET Framework  
  
1.  Kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz **właściwości**.  
  
2.  W **platformy docelowej** listy rozwijanej wybierz odpowiednią wersję.
