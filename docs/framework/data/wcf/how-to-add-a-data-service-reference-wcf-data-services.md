---
title: 'Porady: Dodawanie odwołania do danych usługi (usługi danych WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: a8dcc01fb7a564a363cabed6a22738cd520d317f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>Porady: Dodawanie odwołania do danych usługi (usługi danych WCF)
Można użyć **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio można dodać odwołania do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]. Dzięki temu można łatwiej dostępu do usługi danych w aplikacji klienckiej, która opracowywania w programie Visual Studio. Po zakończeniu tej procedury, klas danych są generowane na podstawie metadanych, które są uzyskiwane z usługi data. Aby uzyskać więcej informacji, zobacz [generowania biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
### <a name="to-add-a-data-service-reference"></a>Aby dodać odwołania do usługi danych  
  
1.  (Opcjonalnie) Jeśli usługa danych nie jest częścią rozwiązania i nie jest już uruchomiona, uruchom usługę danych i Zanotuj identyfikator URI usługi danych.  
  
2.  Kliknij prawym przyciskiem myszy projekt klienta, a następnie wybierz **Dodaj odwołanie do usługi**.  
  
3.  Usługi danych jest częścią bieżącego rozwiązania, kliknij przycisk **odnajdowania**.  
  
     —lub—  
  
     W **adres** polu tekstowym, wpisz podstawowy adres URL usługi danych, takich jak `http://localhost:1234/Northwind.svc`, a następnie kliknij przycisk **Przejdź**.  
  
4.  Kliknij przycisk **OK**.  
  
     Spowoduje to dodanie nowego pliku kodu zawierającego klas danych, które są używane do uzyskania dostępu i interakcji z zasobami usługi danych jako obiekty.  
  
## <a name="see-also"></a>Zobacz też  
 [Szybki start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
