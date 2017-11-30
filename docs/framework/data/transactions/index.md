---
title: Przetwarzanie transakcji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5248dd3a4da450e411dd5d9a7843df6c9263026e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-processing"></a><span data-ttu-id="23177-102">Przetwarzanie transakcji</span><span class="sxs-lookup"><span data-stu-id="23177-102">Transaction Processing</span></span>
<span data-ttu-id="23177-103">Kupując książki z księgarni online, wymieniać się pieniądze (w formie kredytu) książki.</span><span class="sxs-lookup"><span data-stu-id="23177-103">When you purchase a book from an online bookstore, you exchange money (in the form of credit) for a book.</span></span> <span data-ttu-id="23177-104">Jeśli Twój kredytowej jest dobra, serii powiązanych operacji zapewnia, że Pobierz książkę o i księgarni pobiera pieniądze.</span><span class="sxs-lookup"><span data-stu-id="23177-104">If your credit is good, a series of related operations ensures that you get the book and the bookstore gets your money.</span></span> <span data-ttu-id="23177-105">Jednak w przypadku niepowodzenia podczas wymiany jednej operacji w serii całego exchange nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="23177-105">However, if a single operation in the series fails during the exchange, the entire exchange fails.</span></span> <span data-ttu-id="23177-106">Użytkownik nie może korzystać książki i księgarni nie otrzymać pieniądze.</span><span class="sxs-lookup"><span data-stu-id="23177-106">You do not get the book and the bookstore does not get your money.</span></span>  
  
 <span data-ttu-id="23177-107">Technologia odpowiedzialnych za udostępnianie wymiany zrównoważona i przewidywalne jest wywoływana przetwarzania transakcji.</span><span class="sxs-lookup"><span data-stu-id="23177-107">The technology responsible for making the exchange balanced and predictable is called transaction processing.</span></span> <span data-ttu-id="23177-108">Transakcje upewnij się, że dotyczący danych zasobów nie są trwałe aktualizowane chyba, że wszystkie operacje w jednostce transakcyjne pomyślnie ukończona.</span><span class="sxs-lookup"><span data-stu-id="23177-108">Transactions ensure that data-oriented resources are not permanently updated unless all operations within the transactional unit complete successfully.</span></span> <span data-ttu-id="23177-109">Łącząc zestawu powiązanych operacji do jednostki, która całkowicie zakończy się pomyślnie lub całkowicie nie powiedzie się, można uprościć odzyskiwania po błędzie i wprowadzić aplikacji bardziej niezawodne.</span><span class="sxs-lookup"><span data-stu-id="23177-109">By combining a set of related operations into a unit that either completely succeeds or completely fails, you can simplify error recovery and make your application more reliable.</span></span>  
  
 <span data-ttu-id="23177-110">Systemy przetwarzania transakcji składają się z komputera sprzętu i oprogramowania hosting aplikacji zorientowany transakcyjnie, który wykonuje transakcji procedury niezbędne do prowadzenia działalności.</span><span class="sxs-lookup"><span data-stu-id="23177-110">Transaction processing systems consist of computer hardware and software hosting a transaction-oriented application that performs the routine transactions necessary to conduct business.</span></span> <span data-ttu-id="23177-111">Przykładami systemów, które zarządzać wpis zamówienia, rezerwacji linii lotniczych, Lista płac i pracownikach produkcyjny i wysyłania.</span><span class="sxs-lookup"><span data-stu-id="23177-111">Examples include systems that manage sales order entry, airline reservations, payroll, employee records, manufacturing, and shipping.</span></span>  
  
 <span data-ttu-id="23177-112">Ta sekcja zawiera ogólne informacje na temat przetwarzania transakcji i określone informacje na temat sposobu pisania aplikacji transakcyjnych i menedżerowie zasobów przy użyciu programu Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="23177-112">This section provides both general information on transaction processing, and specific information on how to write transactional applications and resource managers using the Microsoft .NET Framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23177-113">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="23177-113">In This Section</span></span>  
 [<span data-ttu-id="23177-114">Podstawowe informacje dotyczące transakcji</span><span class="sxs-lookup"><span data-stu-id="23177-114">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 <span data-ttu-id="23177-115">Wprowadzono podstawowe transakcji przetwarzania terminy i pojęcia.</span><span class="sxs-lookup"><span data-stu-id="23177-115">Introduces basic transaction processing terms and concepts.</span></span>  
  
 [<span data-ttu-id="23177-116">Funkcje oferowane przez bibliotekę System.Transactions</span><span class="sxs-lookup"><span data-stu-id="23177-116">Features Provided by System.Transactions</span></span>](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 <span data-ttu-id="23177-117">W tym artykule omówiono, jak używać funkcji w System.Transactions zapisu transakcyjnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23177-117">Discusses how you can use features in System.Transactions to write your own transactional application.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="23177-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="23177-118">Reference</span></span>  
 <xref:System.Transactions>  
 <span data-ttu-id="23177-119">Udostępnia klasy, które pozwalają na uczestniczenie w transakcjach kodu.</span><span class="sxs-lookup"><span data-stu-id="23177-119">Provides classes that allow your code to participate in transactions.</span></span> <span data-ttu-id="23177-120">Klasy obsługi transakcji z wielu uczestników rozproszonych, wieloma powiadomieniami i trwałych rejestracji.</span><span class="sxs-lookup"><span data-stu-id="23177-120">The classes support transactions with multiple distributed participants, multiple phase notifications, and durable enlistments.</span></span>
