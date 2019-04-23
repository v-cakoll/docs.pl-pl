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
ms.openlocfilehash: 2a4915796310e4f6899d833f20bc5260e0ee032b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171037"
---
# <a name="creating-internet-requests"></a>Tworzenie żądań internetowych
Tworzenie aplikacji <xref:System.Net.WebRequest> wystąpień za pośrednictwem <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody. Jest to metoda statyczna, który tworzy klasę pochodną **WebRequest** oparte na schemat identyfikatora URI przekazywany do niego.  
  
## <a name="web-file-and-ftp-requests"></a>W sieci Web, plików i żądań FTP  
 Program .NET Framework oferuje <xref:System.Net.HttpWebRequest> klasy, która jest pochodną **WebRequest**, do obsługi żądań HTTP i HTTPS. W większości przypadków **WebRequest** klasa udostępnia wszystkie właściwości, musisz wysłać żądanie; Jednakże, jeśli to konieczne, można rzutować **WebRequest** obiekty utworzone przez **WebRequest.Create**  metody **HttpWebRequest** typ, aby uzyskać dostęp do właściwości specyficzne dla protokołu HTTP żądania. Podobnie **HttpWebResponse** obiektu obsługuje odpowiedzi z żądań HTTP i HTTPS. Aby uzyskać dostęp do właściwości specyficzne dla protokołu HTTP z **HttpWebResponse** obiektu, należy rzutować **elementu WebResponse** obiekty do **HttpWebResponse** typu.  
  
 .NET Framework udostępnia również <xref:System.Net.FileWebRequest> i <xref:System.Net.FileWebResponse> klasy do obsługi żądań zasobów, które używają "plików:" Schemat identyfikatora URI. Podobnie <xref:System.Net.FtpWebRequest> i <xref:System.Net.FtpWebResponse> klasy są dostarczane do obsługi żądań zasobów, które używają "ftp:" schematu. Jeśli żądanie jest dla zasobu, który wykorzystuje dowolne z tych systemów, możesz użyć **WebRequest.Create** metody do uzyskiwania obiektu, z którą ma zostać Prześlij żądanie.  
  
 Do obsługi żądań, które używają inne protokoły poziomu aplikacji, którą należy wdrożyć klasy pochodne klasy specyficzne dla protokołu **WebRequest** i **elementu WebResponse**. Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](../../../docs/framework/network-programming/programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Żądanie danych przy użyciu klasy WebRequest](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
- [Żądanie danych](../../../docs/framework/network-programming/requesting-data.md)
