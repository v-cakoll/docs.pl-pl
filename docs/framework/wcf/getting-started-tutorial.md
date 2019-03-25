---
title: 'Samouczek: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation'
description: W tych samouczkach przedstawiono wprowadzenie do tworzenia aplikacji WCF.
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 66211cfcf2b742e43eccbefb2bc7c4bd1147b05b
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408863"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>Samouczek: Rozpoczynanie pracy z aplikacjami Windows Communication Foundation
Poniższą sekwencję samouczki zawierają wprowadzenie do Windows Communication Foundation (WCF) środowisko programowania. Pracy przy użyciu tych samouczków, w kolejności zapewni wprowadzające zrozumienia czynności wymagane do tworzenia aplikacji WCF. Po zakończeniu będziesz mieć uruchomioną usługę WCF i klienta WCF, który wywołuje usługę. 

W samouczku przyjęto założenie, że używasz programu Visual Studio jako środowisko projektowe. Jeśli używasz innego środowiska deweloperskiego, zignorować instrukcje dotyczące programu Visual Studio. 

Dla przykładowych aplikacji WCF, które można pobierać i uruchamiać, zobacz [przykładów Windows Communication Foundation](samples/index.md). Wprowadzenie do przykładów, zobacz [przykładowe wprowadzające](samples/getting-started-sample.md).

Aby uzyskać bardziej szczegółowe informacje o sposobie tworzenia usług i klientów, zobacz [programowanie WCF podstawowe](basic-wcf-programming.md).

## <a name="wcf-tutorials"></a>Samouczki programu WCF

Pierwszych trzech samouczków opisano, jak definiowanie kontraktu usługi WCF, sposobie jego implementowania i sposobu hostowania go. Usługa tworzona jest samodzielnie hostowany w aplikacji konsoli. You can also host services under Microsoft Internet Information Services (IIS). Aby uzyskać więcej informacji, zobacz [jak: Hostowanie usługi WCF w programie IIS](feature-details/how-to-host-a-wcf-service-in-iis.md). Mimo że kod jest używane do konfigurowania usługi w tym samouczku, można również [skonfigurować usługi w pliku konfiguracji](configuring-services-using-configuration-files.md). 

- [Samouczek: Definiowanie kontraktu usługi](how-to-define-a-wcf-service-contract.md)

    Możesz utworzyć kontraktu usługi WCF z interfejsem użytkownika. Ten kontrakt definiuje funkcje, które uwidacznia usługa.

- [Samouczek: Implementowanie kontraktu usługi](how-to-implement-a-wcf-contract.md)

    Po zdefiniowaniu kontrakt, należy zaimplementować go za pomocą klasy usługi.

- [Samouczek: Hostowanie i uruchamianie podstawowej usługi](how-to-host-and-run-a-basic-wcf-service.md)

    Skonfiguruj punkt końcowy usługi i Hostuj usługi w aplikacji konsoli. Dla usługi stanie się aktywna można ją skonfigurować, a następnie Hostuj go w środowisku uruchomieniowym. To środowisko wykonawczej tworzy usługi i kontroluje jego kontekstu i okresu istnienia.

W dwóch następnych samouczków opisano, jak tworzyć, konfigurować i przedstawia użycie aplikacji klienckiej, wywoływania operacji usługi. Usługi publikowania metadanych, który definiuje informacje, które aplikacja kliencka musi komunikować się z usługą. Visual Studio automatyzuje proces uzyskiwania dostępu do metadanych i używa ich do utworzenia aplikacji klienckiej dla usługi. Jeśli zdecydujesz się nie należy używać programu Visual Studio, możesz użyć [narzędzia narzędzie metadanych elementu ServiceModel (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md) zamiast tego.

- [Samouczek: Tworzenie klienta](how-to-create-a-wcf-client.md)

    Pobieranie metadanych tworzenia serwer proxy klienta WCF z usługą WCF. Pobieranie metadanych przy użyciu programu Visual Studio, aby dodać odwołanie do usługi lub narzędzia narzędzie metadanych elementu ServiceModel. Należy określić punkt końcowy, który klient używa w celu uzyskania dostępu do usługi.

- [Samouczek: Używanie klienta](how-to-use-a-wcf-client.md)

    Serwer proxy klienta WCF umożliwia wywoływanie operacji usługi.

## <a name="reference"></a>Tematy pomocy

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>Zobacz także

- [Omówienie pojęć](conceptual-overview.md)
- [Przewodnik po dokumentacji](guide-to-the-documentation.md)
- [Co to jest Windows Communication Foundation](whats-wcf.md)
- [Szczegóły funkcji WCF](feature-details/index.md)
- [Podstawowy cykl życia programowania](basic-programming-lifecycle.md)
- [Kompilowanie klientów](building-clients.md)
- [Podstawy programowania programu WCF](basic-wcf-programming.md)
- [Instrukcje: Tworzenie kontraktu dwukierunkowego](feature-details/how-to-create-a-duplex-contract.md)
- [Instrukcje: Dostęp do usług za pomocą kontraktu dwukierunkowego](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Narzędzie narzędzie metadanych elementu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Instrukcje: Używanie Svcutil.exe do pobierania dokumentów metadanych](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [Instrukcje: Publikowanie metadanych dla usługi przy użyciu pliku konfiguracji](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [Konfigurowanie usług i klientów za pomocą powiązań](using-bindings-to-configure-services-and-clients.md)
- [Wprowadzenie — przykład](samples/getting-started-sample.md)
- [Przykłady Windows Communication Foundation](samples/index.md)
- [Host samodzielny](samples/self-host.md)


