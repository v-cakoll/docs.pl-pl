---
title: Podstawowy cykl życia programowania
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: fe578ba3c655c9c9ea8398b9b2e4d4f974153c8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320826"
---
# <a name="basic-programming-lifecycle"></a>Podstawowy cykl życia programowania
Windows Communication Foundation (WCF) umożliwia aplikacjom komunikowanie się, czy znajdują się na tym samym komputerze, za pośrednictwem Internetu czy na różnych platformach aplikacji. Ten temat zawiera opis zadań, które są wymagane do utworzenia aplikacji WCF. Aby uzyskać działającą przykładową aplikację, zobacz [samouczek wprowadzenie](getting-started-tutorial.md).  
  
## <a name="the-basic-tasks"></a>Podstawowe zadania  
 Podstawowe zadania do wykonania to:  
  
1. Zdefiniuj kontrakt usługi. Kontrakt usługi określa sygnaturę usługi, dane, które wymienia, oraz inne dane wymagane z umową. Aby uzyskać więcej informacji, zobacz [Projektowanie kontraktów usług](designing-service-contracts.md).  
  
2. Zaimplementuj kontrakt. Aby zaimplementować kontrakt usługi, należy utworzyć klasę, która implementuje kontrakt i określić zachowania niestandardowe, które powinien mieć środowisko uruchomieniowe. Aby uzyskać więcej informacji, zobacz [implementowanie kontraktów usług](implementing-service-contracts.md).  
  
3. Skonfiguruj usługę, określając punkty końcowe i inne informacje o zachowaniu. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług](configuring-services.md).  
  
4. Hostowanie usługi. Aby uzyskać więcej informacji, zobacz [usługi hostingu](hosting-services.md).  
  
5. Tworzenie aplikacji klienckiej. Aby uzyskać więcej informacji, zobacz [Kompilowanie klientów](building-clients.md).  
  
 Mimo że tematy w tej sekcji są zgodne z tą kolejnością, niektóre scenariusze nie zaczynają się od początku. Na przykład jeśli chcesz skompilować klienta dla istniejącej usługi, Zacznij od kroku 5. Lub jeśli tworzysz usługę, która będzie używana przez inne osoby, możesz pominąć krok 5.  
  
 Po zapoznaniu się z projektowaniem kontraktów usług można także zapoznać [się z wprowadzeniem do rozszerzalności](introduction-to-extensibility.md). Jeśli masz problemy z usługą, sprawdź rozwiązanie do [rozwiązywania problemów](wcf-troubleshooting-quickstart.md) z programem WCF, aby sprawdzić, czy inne osoby mają takie same lub podobne problemy.  
  
## <a name="see-also"></a>Zobacz także

- [Implementowanie kontraktów usług](implementing-service-contracts.md)
