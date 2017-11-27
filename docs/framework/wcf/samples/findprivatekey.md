---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c1ff00bead6130601070ac94686ee9622a6fe218
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="findprivatekey"></a>FindPrivateKey
Może być trudne znaleźć lokalizację i nazwę pliku klucza prywatnego skojarzonego z certyfikatem X.509 określonej w magazynie certyfikatów. Narzędzie FindPrivateKey.exe ułatwia ten proces.  
  
> [!IMPORTANT]
>  FindPrivateKey to przykład, który musi być skompilowany przed ich użyciem. Zobacz "Aby skompilować projekt FindPrivateKey" poniższą sekcję, aby uzyskać instrukcje na temat sposobu FindPrivateKey narzędzie kompilacji.  
  
 Certyfikaty X.509 są instalowane przez administratora lub dowolnego użytkownika na maszynie. Jednak certyfikat mogą być używane przez usługę uruchomiony przy użyciu innego konta (na przykład ASPNET na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] lub konta usługi SIECIOWEJ na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).  
  
 To konto może nie mieć dostępu do pliku klucza prywatnego, ponieważ certyfikat nie został zainstalowany przez nią pierwotnie. FindPrivateKey udostępnia lokalizację pliku klucza prywatnego danego certyfikatu X.509. Można dodać uprawnienia lub usunąć uprawnienia do tego pliku, znając lokalizację certyfikatów X.509 określonego pliku klucza prywatnego.  
  
 Przykłady, które korzystają z certyfikatów do zabezpieczenia narzędzie FindPrivateKey w pliku Setup.bat pliku. Po można odnaleźć pliku klucza prywatnego można użyć innych narzędzi, takich jak Cacls.exe, aby ustawić odpowiednie uprawnienia dostępu do pliku.  
  
 Podczas uruchamiania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi przy użyciu konta użytkownika, takie jak hostowanie Samoobsługowe pliku wykonywalnego, upewnij się, że konto użytkownika ma dostęp tylko do odczytu do pliku. Podczas uruchamiania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi w obszarze Internet Information Services (IIS) domyślne konta, które usługa będzie uruchamiana są ASPNET na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] lub NETWORK SERVICE w [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], które domyślnie nie mają dostępu do pliku klucza prywatnego.  
  
## <a name="examples"></a>Przykłady  
 Podczas uzyskiwania dostępu do certyfikatu, dla którego proces nie ma uprawnień odczytu, zobaczysz komunikat o wyjątku podobny do poniższego przykładu.  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 W takim przypadku należy użyć narzędzia FindPrivateKey można znaleźć pliku klucza prywatnego, a następnie ustaw dostępu dla procesu, czy usługa jest uruchomiona w obszarze odpowiedni. Na przykład można to zrobić za pomocą narzędzia Cacls.exe jak pokazano w poniższym przykładzie.  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a>Aby skompilować projekt FindPrivateKey  
  
1.  Otwórz [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] i przejdź do podkatalogu specyficzne dla języka w obszarze na lokalizację katalogu, w którym zainstalowano próbki.  
  
2.  Kliknij dwukrotnie ikonę pliku SLN, można otworzyć pliku w programie Visual Studio.  
  
3.  W **kompilacji** menu, wybierz opcję **Kompiluj ponownie rozwiązanie**. Pliki programu klienta są przeznaczone do client\bin i pliki programu usługi są przeznaczone do service\bin.  
  
4.  Tworzenie rozwiązania generuje plik: FindPrivateKey.exe.  
  
## <a name="conventionscommand-line-entries"></a>Konwencje — wpisy wiersza polecenia  
 "[*opcji*]" reprezentuje opcjonalny zestaw parametrów.  
  
 "{*opcji*}" reprezentuje obowiązkowe zestaw parametrów.  
  
 "*opcja 1* &#124; *option2*"reprezentuje wybór między Ustawia opcje.  
  
 "\<*wartość*>" reprezentuje należy podać wartość parametru.  
  
## <a name="usage"></a>Użycie  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 Gdzie:  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 Jeśli nie określono żadnych parametrów w wierszu polecenia, zostanie wyświetlony ten tekst pomocy.  
  
## <a name="examples"></a>Przykłady  
 W tym przykładzie znajdzie pliku certyfikatu z nazwą podmiotu "CN = host_lokalny", w magazynie osobistym z bieżącym CurrentUser Moje User.FindPrivateKey - n "CN = localhost".  
  
 W tym przykładzie znajdzie pliku certyfikatu z nazwą podmiotu "CN = host_lokalny", w osobistych przechowywać bieżącego i dane wyjściowe pełną ścieżką.  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 W tym przykładzie znajdzie nazwę certyfikatu z odciskiem palca "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1 d 6b 52", w magazynie osobistym komputera lokalnego.  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a>Zobacz też
