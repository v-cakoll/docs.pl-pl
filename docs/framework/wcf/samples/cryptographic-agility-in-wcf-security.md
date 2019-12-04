---
title: Elastyczność kryptograficzna w zabezpieczeniach WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 2dbacd53876ded76ea212dd5656cd2dded4a6e48
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714924"
---
# <a name="cryptographic-agility-in-wcf-security"></a>Elastyczność kryptograficzna w zabezpieczeniach WCF

Ten przykład pokazuje, jak określić w algorytmie Standard/Custom, aby zapewnić kryptograficzną implementację Agile w ramach klienta i usługi Windows Communication Foundation (WCF). Przykład składa się z następujących projektów:

**Usługa**

Jest to samodzielna usługa WCF, która implementuje interfejs `ICalculator` i zabezpiecza punkt końcowy przy użyciu <xref:System.ServiceModel.WSHttpBinding> z obsługą bezpiecznej sesji i niezawodnej sesji. Usługa definiuje niestandardową klasę `SecurityAlgorithmSuite`, aby określić algorytmy kryptograficzne, które mają być używane na potrzeby zabezpieczeń komunikatów.

**Klient**

Jest to klient WCF, który uzyskuje dostęp do usługi po pomyślnym uwierzytelnieniu. Wywołuje operacje udostępniane przez interfejs `ICalculator` i implementowane przez usługę. Klient definiuje również tę samą niestandardową klasę `SecurityAlgorithmSuite`, aby określić algorytmy kryptograficzne, które mają być używane na potrzeby zabezpieczeń komunikatów.

## <a name="to-use-this-sample"></a>Aby użyć tego przykładu

1. Otwórz rozwiązanie CryptoAgility. sln w programie Visual Studio 2012.

2. Naciśnij kombinację klawiszy CTRL + SHIFT + B, aby skompilować rozwiązanie.

3. Otwórz Eksploratora plików i przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Service\bin i uruchom plik Service. exe z uprawnieniami administratora, klikając prawym przyciskiem myszy pozycję Service. exe i wybierając polecenie **Uruchom jako administrator**.

4. Przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Client\bin i uruchom plik Client. exe normalnie.

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia Windows Communication Foundation](../feature-details/security.md)
