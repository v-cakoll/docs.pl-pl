---
title: Tworzenie żądań internetowych
description: Dowiedz się, jak aplikacje tworzą wystąpienia WebRequest za pośrednictwem WebRequest. Create, metoda statyczna, która tworzy klasę pochodną opartą na schemacie URI przekazaną do niego.
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
ms.openlocfilehash: 598ef9d44737ef6b33af833cbfb7788170165588
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502629"
---
# <a name="creating-internet-requests"></a>Tworzenie żądań internetowych
Aplikacje tworzą <xref:System.Net.WebRequest> wystąpienia za pomocą <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody. Jest to metoda statyczna, która tworzy klasę pochodną od **żądania WebRequest** na podstawie schematu identyfikatora URI, do którego został przesłany.  
  
## <a name="web-file-and-ftp-requests"></a>Żądania sieci Web, plików i FTP  
 .NET Framework dostarcza <xref:System.Net.HttpWebRequest> klasę, która pochodzi od **żądania WebRequest**, do obsługi żądań HTTP i https. W większości przypadków Klasa **WebRequest** zawiera wszystkie właściwości potrzebne do zgłoszenia żądania. Jednak w razie potrzeby można rzutować obiekty **WebRequest** utworzone przez metodę **WebRequest. Create** na typ **HttpWebRequest** , aby uzyskać dostęp do właściwości żądania specyficznego dla protokołu HTTP. Podobnie obiekt **HttpWebResponse** obsługuje odpowiedzi z żądań HTTP i https. Aby uzyskać dostęp do właściwości specyficznych dla protokołu HTTP obiektu **HttpWebResponse** , należy rzutować obiekty **WebResponse** na typ **HttpWebResponse** .  
  
 .NET Framework udostępnia również <xref:System.Net.FileWebRequest> <xref:System.Net.FileWebResponse> klasy i obsługujące żądania dla zasobów, które używają schematu identyfikatora URI "File:". Podobnie <xref:System.Net.FtpWebRequest> <xref:System.Net.FtpWebResponse> klasy i są udostępniane do obsługi żądań dotyczących zasobów, które używają schematu "FTP:". Jeśli Twoje żądanie dotyczy zasobu korzystającego z dowolnego z tych schematów, można użyć metody **WebRequest. Create** w celu uzyskania obiektu, z którym ma zostać wysłane żądanie.  
  
 Aby obsługiwać żądania korzystające z innych protokołów na poziomie aplikacji, należy zaimplementować klasy specyficzne dla protokołu pochodzące z **WebRequest** i **WebResponse**. Aby uzyskać więcej informacji, zobacz [programowanie protokołów podłączanych](programming-pluggable-protocols.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: żądanie danych przy użyciu klasy WebRequest](how-to-request-data-using-the-webrequest-class.md)
- [Żądanie danych](requesting-data.md)
