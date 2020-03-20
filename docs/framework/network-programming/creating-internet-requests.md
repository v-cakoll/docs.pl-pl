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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048620"
---
# <a name="creating-internet-requests"></a>Tworzenie żądań internetowych
Aplikacje <xref:System.Net.WebRequest> tworzą wystąpienia <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> za pomocą metody. Jest to metoda statyczna, która tworzy klasę pochodną **WebRequest** na podstawie schematu URI przekazany do niego.  
  
## <a name="web-file-and-ftp-requests"></a>Żądania sieci Web, plików i FTP  
 .NET Framework udostępnia <xref:System.Net.HttpWebRequest> klasę, która jest pochodną **WebRequest**, do obsługi żądań HTTP i HTTPS. W większości przypadków **WebRequest** klasa zapewnia wszystkie właściwości potrzebne do żądania; jednak w razie potrzeby można rzutować **WebRequest** obiektów utworzonych przez **WebRequest.Create** metody do **HttpWebRequest** typu dostępu do właściwości specyficznych dla protokołu HTTP żądania. Podobnie obiekt **HttpWebResponse** obsługuje odpowiedzi z żądań HTTP i HTTPS. Aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP **HttpWebResponse** obiektu, należy rzutować **WebResponse** obiektów do **httpWebResponse** typu.  
  
 .NET Framework udostępnia <xref:System.Net.FileWebRequest> również <xref:System.Net.FileWebResponse> i klasy do obsługi żądań dla zasobów, które używają schematu URI "file:". Podobnie <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy są dostarczane do obsługi żądań dla zasobów, które używają schematu "ftp:". Jeśli żądanie dotyczy zasobu, który używa dowolnego z tych schematów, można użyć **WebRequest.Create** metody, aby uzyskać obiekt, za pomocą którego można złożyć żądanie.  
  
 Aby obsłużyć żądania korzystające z innych protokołów na poziomie aplikacji, należy zaimplementować klasy specyficzne dla protokołu pochodzące z **WebRequest** i **WebResponse**. Aby uzyskać więcej informacji, zobacz [Programowanie protokołów podłączanych](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: żądanie danych przy użyciu klasy WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Żądanie danych](requesting-data.md)
