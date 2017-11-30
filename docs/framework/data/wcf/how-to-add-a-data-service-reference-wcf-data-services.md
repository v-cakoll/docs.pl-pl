---
title: "Porady: Dodawanie odwołania do danych usługi (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8fb075bdb17f0d562d752bc4125141bb0bb2ab9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
 [Szybki Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
