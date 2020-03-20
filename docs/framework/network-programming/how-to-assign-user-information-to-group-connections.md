---
title: 'Instrukcje: przypisywanie informacji użytkownika do połączeń grupowych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ce550d6-8f7c-4ea7-add8-5bc27a7b51be
ms.openlocfilehash: 01b686702250c68131e8a46b410ce05e67e7c950
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180844"
---
# <a name="how-to-assign-user-information-to-group-connections"></a><span data-ttu-id="15d2e-102">Instrukcje: przypisywanie informacji użytkownika do połączeń grupowych</span><span class="sxs-lookup"><span data-stu-id="15d2e-102">How to: Assign User Information to Group Connections</span></span>

 <span data-ttu-id="15d2e-103">W poniższym przykładzie pokazano, jak przypisać informacje o użytkowniku do połączeń grupowych, przy założeniu, że aplikacja ustawia zmienne *UserName*, *SecurelyStoredPassword*i *Domain* przed wywołaniem tej sekcji kodu i że *Nazwa użytkownika* jest unikatowa.</span><span class="sxs-lookup"><span data-stu-id="15d2e-103">The following example demonstrates how to assign user information to group connections, assuming that the application sets the variables *UserName*, *SecurelyStoredPassword*, and *Domain* before this section of code is called and that *UserName* is unique.</span></span>  
  
### <a name="to-assign-user-information-to-a-group-connection"></a><span data-ttu-id="15d2e-104">Aby przypisać informacje o użytkowniku do połączenia grupowego</span><span class="sxs-lookup"><span data-stu-id="15d2e-104">To assign user information to a group connection</span></span>  
  
1. <span data-ttu-id="15d2e-105">Tworzenie nazwy grupy połączeń.</span><span class="sxs-lookup"><span data-stu-id="15d2e-105">Create a connection group name.</span></span>  
  
    ```csharp  
    SHA1Managed Sha1 = new SHA1Managed();  
    Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
    String secureGroupName = Encoding.Default.GetString(updHash);  
    ```  
  
    ```vb  
    Dim Sha1 As New SHA1Managed()  
    Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
    Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
    ```  
  
2. <span data-ttu-id="15d2e-106">Utwórz żądanie określonego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="15d2e-106">Create a request for a specific URL.</span></span> <span data-ttu-id="15d2e-107">Na przykład poniższy kod tworzy żądanie dla adresu URL`http://www.contoso.com.`</span><span class="sxs-lookup"><span data-stu-id="15d2e-107">For example, the following code creates a request for the URL `http://www.contoso.com.`</span></span>  
  
    ```csharp  
    WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
    ```  
  
    ```vb  
    Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
    ```  
  
3. <span data-ttu-id="15d2e-108">Ustaw poświadczenia i nazwa grupy połączeń dla żądania sieci Web i zadzwoń do **getresponse,** aby pobrać obiekt **WebResponse.**</span><span class="sxs-lookup"><span data-stu-id="15d2e-108">Set the credentials and Connection GroupName for the Web request, and call **GetResponse** to retrieve a **WebResponse** object.</span></span>  
  
    ```csharp  
    myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);
    myWebRequest.ConnectionGroupName = secureGroupName;  
  
    WebResponse myWebResponse=myWebRequest.GetResponse();  
    ```  
  
    ```vb  
    myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
    myWebRequest.ConnectionGroupName = secureGroupName  
  
    Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
    ```  
  
4. <span data-ttu-id="15d2e-109">Zamknij strumień odpowiedzi po użyciu obiektu WebRespose.</span><span class="sxs-lookup"><span data-stu-id="15d2e-109">Close the response stream after using the WebRespose object.</span></span>  
  
    ```csharp  
    MyWebResponse.Close();  
    ```  
  
    ```vb  
    MyWebResponse.Close()  
    ```  
  
 <span data-ttu-id="15d2e-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="15d2e-110">Example</span></span>  
  
```csharp  
// Create a connection group name.  
SHA1Managed Sha1 = new SHA1Managed();  
Byte[] updHash = Sha1.ComputeHash(Encoding.UTF8.GetBytes(UserName + SecurelyStoredPassword + Domain));  
String secureGroupName = Encoding.Default.GetString(updHash);  
  
// Create a request for a specific URL.  
WebRequest myWebRequest=WebRequest.Create("http://www.contoso.com");  
  
myWebRequest.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword, Domain);
myWebRequest.ConnectionGroupName = secureGroupName;  
  
WebResponse myWebResponse=myWebRequest.GetResponse();  
  
// Insert the code that uses myWebResponse.  
  
MyWebResponse.Close();  
```  
  
```vb  
' Create a secure group name.  
Dim Sha1 As New SHA1Managed()  
Dim updHash As [Byte]() = Sha1.ComputeHash(Encoding.UTF8.GetBytes((UserName + SecurelyStoredPassword + Domain)))  
Dim secureGroupName As [String] = Encoding.Default.GetString(updHash)  
  
' Create a request for a specific URL.  
Dim myWebRequest As WebRequest = WebRequest.Create("http://www.contoso.com")  
  
myWebRequest.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
myWebRequest.ConnectionGroupName = secureGroupName  
  
Dim myWebResponse As WebResponse = myWebRequest.GetResponse()  
  
' Insert the code that uses myWebResponse.  
MyWebResponse.Close()  
```  
  
## <a name="see-also"></a><span data-ttu-id="15d2e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15d2e-111">See also</span></span>

- [<span data-ttu-id="15d2e-112">Zarządzanie połączeniami</span><span class="sxs-lookup"><span data-stu-id="15d2e-112">Managing Connections</span></span>](managing-connections.md)
- [<span data-ttu-id="15d2e-113">Grupowanie połączeń</span><span class="sxs-lookup"><span data-stu-id="15d2e-113">Connection Grouping</span></span>](connection-grouping.md)
