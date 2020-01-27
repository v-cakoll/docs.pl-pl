---
title: Modele transakcji
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: d6c78a5342bf19d19308352cddc241f436bfcb3a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745323"
---
# <a name="transaction-models"></a>Modele transakcji
W tym temacie opisano relację między modelami programowania transakcji i składnikami infrastruktury dostarczanymi przez firmę Microsoft.  
  
 W przypadku korzystania z transakcji w programie Windows Communication Foundation (WCF) ważne jest, aby zrozumieć, że nie są wybierane między różnymi modelami transakcyjnymi, ale raczej działają na różnych warstwach zintegrowanego i spójnego modelu.  
  
 W poniższych sekcjach opisano trzy podstawowe składniki transakcji.  
  
## <a name="windows-communication-foundation-transactions"></a>Windows Communication Foundation transakcji  
 Obsługa transakcji w programie WCF umożliwia zapisywanie usług transakcyjnych. Ponadto wraz z obsługą protokołu WS-AtomicTransaction (WS-AT) aplikacje mogą przepływać transakcje do usług sieci Web zbudowanych przy użyciu technologii WCF i innych firm.  
  
 W usłudze lub aplikacji WCF funkcje transakcji WCF zapewniają atrybuty i konfigurację, aby deklaratywnie określić, jak i kiedy infrastruktura ma tworzyć, przepływać i synchronizować transakcje.  
  
## <a name="systemtransactions-transactions"></a>Transakcje system. Transactions  
 Przestrzeń nazw <xref:System.Transactions> zapewnia jawny model programowania oparty na klasie <xref:System.Transactions.Transaction>, a także niejawny model programowania korzystający z klasy <xref:System.Transactions.TransactionScope>, w której infrastruktura automatycznie zarządza transakcjami.  
  
 Aby uzyskać więcej informacji na temat tworzenia transakcyjnej aplikacji przy użyciu tych dwóch modeli, zobacz [pisanie aplikacji transakcyjnej](https://go.microsoft.com/fwlink/?LinkId=94947).  
  
 W usłudze lub aplikacji WCF <xref:System.Transactions> zapewnia model programowania do tworzenia transakcji w aplikacji klienckiej i w celu jawnego korzystania z transakcji, w razie potrzeby w ramach usługi.  
  
## <a name="msdtc-transactions"></a>Transakcje usługi MSDTC  
 Microsoft Distributed Transaction Coordinator (MSDTC) to Menedżer transakcji, który zapewnia obsługę transakcji rozproszonych.  
  
 Aby uzyskać więcej informacji, zobacz [Dokumentacja programisty usługi DTC](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108(v=vs.85)).  
  
 W usłudze lub aplikacji WCF usługa MSDTC udostępnia infrastrukturę do koordynacji transakcji utworzonych w ramach klienta lub usługi.
