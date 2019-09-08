---
title: 'Instrukcje: Dodawanie odwołania do usługi danych (Usługi danych programu WCF)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790737"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Instrukcje: Dodawanie odwołania do usługi danych (Usługi danych programu WCF)

Aby dodać odwołanie do Usługi danych programu WCF, można użyć okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio. Dzięki temu można łatwiej uzyskać dostęp do usługi danych w aplikacji klienckiej opracowywanej w programie Visual Studio. Po wykonaniu tej procedury klasy danych są generowane na podstawie metadanych uzyskanych z usługi danych. Aby uzyskać więcej informacji, zobacz [generowanie biblioteki klienta usługi danych](generating-the-data-service-client-library-wcf-data-services.md).

## <a name="add-a-data-service-reference"></a>Dodawanie odwołania do usługi danych

1. Obowiązkowe Jeśli usługa danych nie jest częścią rozwiązania i nie jest już uruchomiona, uruchom usługę danych i zanotuj identyfikator URI usługi danych.

2. W programie Visual Studio w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt klienta, a następnie wybierz polecenie **Dodaj** > **odwołanie do usługi**.

3. Jeśli usługa danych jest częścią bieżącego rozwiązania, kliknij przycisk **odkryj**.

     —lub—

     W polu tekstowym **adres** wpisz podstawowy adres URL usługi danych, `http://localhost:1234/Northwind.svc`na przykład, a następnie kliknij przycisk **Przejdź**.

4. Kliknij przycisk **OK**.

     Nowy plik kodu, który zawiera klasy danych, które mogą uzyskiwać dostęp do zasobów usługi danych i współdziałać z nimi, jest dodawany do projektu.

## <a name="see-also"></a>Zobacz także

- [Szybki start](quickstart-wcf-data-services.md)
