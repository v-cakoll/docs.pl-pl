---
title: 'Porady: Dodawanie odwołania usługi danych (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: fc1786e1c6102c702374989253cd3ce23e3f7b54
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404426"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Porady: Dodawanie odwołania usługi danych (WCF Data Services)

Możesz użyć **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio, aby dodać odwołanie do usługi danych WCF. Dzięki temu można łatwiej uzyskać dostęp do danych usługi w aplikacji klienckiej, który da się opracować w programie Visual Studio. Po ukończeniu tej procedury klas danych są generowane na podstawie metadanych uzyskany z usługi danych. Aby uzyskać więcej informacji, zobacz [Generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

## <a name="add-a-data-service-reference"></a>Dodaj odwołanie do usługi danych

1. (Opcjonalnie) Jeśli usługa danych nie jest częścią rozwiązania i nie jest już uruchomiona, uruchom usługę danych i Zanotuj identyfikator URI usługi danych.

2. W programie Visual Studio w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt klienta, a następnie wybierz **Dodaj** > **odwołanie do usługi**.

3. Jeśli usługa danych jest częścią bieżącego rozwiązania, kliknij przycisk **odnajdź**.

     —lub—

     W **adres** polu tekstowym wpisz podstawowy adres URL usługi danych, takich jak `http://localhost:1234/Northwind.svc`, a następnie kliknij przycisk **Przejdź**.

4. Wybierz **OK**.

     Nowy plik kodu, który zawiera klasy danych, które mogą uzyskać dostęp i korzystać z zasobów usługi danych zostanie dodany do projektu.

## <a name="see-also"></a>Zobacz także

- [Szybki start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)