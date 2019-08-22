---
title: Użycie domyślnego wystąpienia klasy w konstruktorze klas może prowadzić do nieskończonego wywołania cyklicznego
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cec3d3d462822ca571cab59a2e4d7e730d2aec46
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664366"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>Użycie domyślnego wystąpienia klasy w konstruktorze klas może prowadzić do nieskończonego wywołania cyklicznego
W konstruktorze klasy użyto domyślnego wystąpienia klasy. Może to prowadzić do nieskończonego wywołania cyklicznego, nazywanego również pętlą nieskończoną.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Usuń wystąpienie domyślne z konstruktora klasy.  
  
## <a name="see-also"></a>Zobacz także

- [Konstruktory](../programming-guide/concepts/object-oriented-programming.md#constructors)
