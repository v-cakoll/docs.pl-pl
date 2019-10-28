---
title: Zasoby systemu operacyjnego wymagane przez architekturę WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: c2c26d769424a8d0655591cb10b4b13df8a15884
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961132"
---
# <a name="operating-system-resources-required-by-wcf"></a>Zasoby systemu operacyjnego wymagane przez architekturę WCF

Windows Communication Foundation (WCF) zależy od kilku zasobów dostarczonych przez system operacyjny do działania. W poniższej tabeli wymieniono te zasoby:

|Zasób|Opis|
|--------------|-----------------|
|Microsoft Distributed Transaction Coordinator (MSDTC)|Wymagane do obsługi transakcji OleTx.|
|Internet Information Services (IIS)|Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.|
|Usługa aktywacji procesów systemu Windows (WAS)|Wymagane, jeśli chcesz używać aplikacji.|
