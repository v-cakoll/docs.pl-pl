---
title: Tworzenie żądań internetowych
ms.date: 03/30/2017
helpviewer_keywords:
- WebRequest class, sending and receiving data
- Networking
- HttpWebResponse class, sending and receiving data
- requesting data from Internet, creating requests
- Network Resources
- Internet, requesting data
- data requests, creating requests
ms.assetid: faab683e-3f1e-4eee-b5e9-59f7245033d5
ms.openlocfilehash: 80e3a6bd199691df9391e88d5a64fab5df2a08a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048620"
---
# <a name="creating-internet-requests"></a>Tworzenie żądań internetowych
Aplikacje tworzą <xref:System.Net.WebRequest> wystąpienia <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> za pomocą metody. Jest to metoda statyczna, która tworzy klasę pochodną od **żądania WebRequest** na podstawie schematu identyfikatora URI, do którego został przesłany.  
  
## <a name="web-file-and-ftp-requests"></a>Żądania sieci Web, plików i FTP  
 .NET Framework dostarcza <xref:System.Net.HttpWebRequest> klasę, która pochodzi od **żądania WebRequest**, do obsługi żądań HTTP i https. W większości przypadków Klasa **WebRequest** zawiera wszystkie właściwości potrzebne do zgłoszenia żądania. Jednak w razie potrzeby można rzutować obiekty **WebRequest** utworzone przez metodę **WebRequest. Create** na typ **HttpWebRequest** , aby uzyskać dostęp do właściwości żądania specyficznego dla protokołu HTTP. Podobnie obiekt **HttpWebResponse** obsługuje odpowiedzi z żądań HTTP i https. Aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP obiektu **HttpWebResponse** , należy rzutować obiekty **WebResponse** na typ **HttpWebResponse** .  
  
 .NET Framework udostępnia <xref:System.Net.FileWebRequest> również klasy i <xref:System.Net.FileWebResponse> obsługujące żądania dla zasobów, które używają "plik:" Schemat identyfikatora URI. Podobnie klasy <xref:System.Net.FtpWebResponse> i są udostępniane do obsługi żądań dotyczących zasobów, które używają schematu "FTP:". <xref:System.Net.FtpWebRequest> Jeśli Twoje żądanie dotyczy zasobu korzystającego z dowolnego z tych schematów, można użyć metody **WebRequest. Create** w celu uzyskania obiektu, z którym ma zostać wysłane żądanie.  
  
 Aby obsługiwać żądania korzystające z innych protokołów na poziomie aplikacji, należy zaimplementować klasy specyficzne dla protokołu pochodzące z **WebRequest** i **WebResponse**. Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Żądanie danych przy użyciu klasy WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Żądanie danych](requesting-data.md)
