---
title: Obsługa integracji AJAX i notacji JSON
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: 3054c3c6faa8dfe621c706d8df031c23d497da0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576515"
---
# <a name="ajax-integration-and-json-support"></a>Obsługa integracji AJAX i notacji JSON
Obsługa Windows Communication Foundation (WCF) dla ASP.NET asynchronicznego języka JavaScript i XML (AJAX) oraz formatu danych JavaScript Object Notation (JSON) umożliwia usługom WCF udostępnianie operacji klientom AJAX. Klienci AJAX są stronami sieci Web, w których uruchomiono kod JavaScript i uzyskują dostęp do tych usług WCF przy użyciu żądań HTTP. Tematy w tej sekcji zawierają informacje o tej pomocy technicznej i sposobach ich implementacji.  
  
 Aby uzyskać więcej informacji na temat ASP.NET AJAX i integracji z ASP.NET 2,0, zobacz [ASP.NET AJAX — Omówienie](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100)).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](creating-wcf-services-for-aspnet-ajax.md)  
 Opisuje, w jaki sposób można uwidocznić usługę WCF klientom AJAX, dodając odpowiedni punkt końcowy AJAX przez konfigurację lub przy użyciu fabryki hosta usługi dostosowanej do wygenerowania hosta usługi, który automatycznie konfiguruje punkt końcowy AJAX.  
  
 [Tworzenie usług AJAX WCF bez platformy ASP.NET](creating-wcf-ajax-services-without-aspnet.md)  
 Zawiera opis sposobu tworzenia usługi WCF bez używania ASP.NET.  
  
 [Obsługa formatu JSON i innych formatów transferowania danych](support-for-json-and-other-data-transfer-formats.md)  
 W tym artykule opisano obsługę formatu JSON, który zwykle jest używany (zamiast XML) do obsługi komunikatów w usłudze ASP.NET AJAX.  
  
 [Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 Opisuje sposób migrowania usługi sieci Web ASP.NET z włączoną obsługą technologii AJAX do usługi sieci Web programu WCF.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [Model programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-model.md)
