---
title: Nieobsługiwane interfejsy API w programie .NET Core
titleSuffix: ''
description: Dowiedz się, które interfejsy API z .NET Framework, które zawsze zgłaszają wyjątek na platformie .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: c4b94321d30cacd90d5c2ee23c258681683a6faa
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092970"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="b1aea-103">Interfejsy API, które zawsze generują wyjątki w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="b1aea-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="b1aea-104">Następujące interfejsy API zawsze będą zgłaszać <xref:System.PlatformNotSupportedException> na platformie .NET Core na wszystkich lub podzestawach platform.</span><span class="sxs-lookup"><span data-stu-id="b1aea-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="b1aea-105">Ten artykuł organizuje elementy członkowskie interfejsu API według przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b1aea-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="b1aea-106">Ten artykuł jest pracą w toku.</span><span class="sxs-lookup"><span data-stu-id="b1aea-106">This article is a work-in-progress.</span></span> <span data-ttu-id="b1aea-107">Nie jest to kompletna lista interfejsów API, które generują wyjątki w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b1aea-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="b1aea-108">Ten artykuł nie zawiera jawnych implementacji interfejsu dla serializacji binarnej, która zgłasza na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b1aea-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="b1aea-109">Aby uzyskać więcej informacji, zobacz [Serializacja binarna w programie .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="b1aea-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="b1aea-110">System</span><span class="sxs-lookup"><span data-stu-id="b1aea-110">System</span></span>

| <span data-ttu-id="b1aea-111">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-111">Member</span></span> | <span data-ttu-id="b1aea-112">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-113">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-114">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="b1aea-115">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="b1aea-116">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-117">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="b1aea-118">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="b1aea-119">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="b1aea-120">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-121">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-122">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="b1aea-123">System. CodeDom. Compiler</span><span class="sxs-lookup"><span data-stu-id="b1aea-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="b1aea-124">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-124">Member</span></span> | <span data-ttu-id="b1aea-125">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-126">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-127">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-128">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="b1aea-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="b1aea-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="b1aea-130">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-130">Member</span></span> | <span data-ttu-id="b1aea-131">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-132">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-133">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-134">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="b1aea-135">System. Configuration</span><span class="sxs-lookup"><span data-stu-id="b1aea-135">System.Configuration</span></span>

| <span data-ttu-id="b1aea-136">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-136">Member</span></span> | <span data-ttu-id="b1aea-137">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b1aea-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (wszystkie elementy członkowskie)</span><span class="sxs-lookup"><span data-stu-id="b1aea-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="b1aea-139">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="b1aea-140">System. Console</span><span class="sxs-lookup"><span data-stu-id="b1aea-140">System.Console</span></span>

| <span data-ttu-id="b1aea-141">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-141">Member</span></span> | <span data-ttu-id="b1aea-142">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="b1aea-143">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-143">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-145">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-145">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-147">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-147">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-149">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-149">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="b1aea-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b1aea-151">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-152">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-153">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-154">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-154">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-155"><xref:System.Console.Title?displayProperty=nameWithType> (tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="b1aea-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b1aea-156">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-156">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-158">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-158">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-160">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-160">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-162">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-162">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-164">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="b1aea-165">System. Data. Common</span><span class="sxs-lookup"><span data-stu-id="b1aea-165">System.Data.Common</span></span>

| <span data-ttu-id="b1aea-166">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-166">Member</span></span> | <span data-ttu-id="b1aea-167">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b1aea-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (zgłasza <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="b1aea-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="b1aea-169">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="b1aea-170">System. Diagnostics. Process</span><span class="sxs-lookup"><span data-stu-id="b1aea-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="b1aea-171">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-171">Member</span></span> | <span data-ttu-id="b1aea-172">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="b1aea-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-174">Linux</span><span class="sxs-lookup"><span data-stu-id="b1aea-174">Linux</span></span> |
| <span data-ttu-id="b1aea-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-176">Linux</span><span class="sxs-lookup"><span data-stu-id="b1aea-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="b1aea-177">macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="b1aea-178">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-179">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="b1aea-180">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="b1aea-181">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="b1aea-182">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="b1aea-183">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-183">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-185">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-185">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (tylko pobieranie)</span><span class="sxs-lookup"><span data-stu-id="b1aea-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="b1aea-187">macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-187">macOS</span></span> |
| <span data-ttu-id="b1aea-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-189">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="b1aea-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="b1aea-190">System.IO</span></span>

| <span data-ttu-id="b1aea-191">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-191">Member</span></span> | <span data-ttu-id="b1aea-192">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-193">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-194">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="b1aea-195">System. IO. Pipes</span><span class="sxs-lookup"><span data-stu-id="b1aea-195">System.IO.Pipes</span></span>

| <span data-ttu-id="b1aea-196">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-196">Member</span></span> | <span data-ttu-id="b1aea-197">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="b1aea-198">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="b1aea-199">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="b1aea-200">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="b1aea-201">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-201">Linux and macOS</span></span> |
| <span data-ttu-id="b1aea-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-203">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="b1aea-204">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="b1aea-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="b1aea-205">System.Media</span></span>

| <span data-ttu-id="b1aea-206">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-206">Member</span></span> | <span data-ttu-id="b1aea-207">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-208">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="b1aea-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="b1aea-209">System.Net</span></span>

| <span data-ttu-id="b1aea-210">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-210">Member</span></span> | <span data-ttu-id="b1aea-211">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-212">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-213">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-214">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-215">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-216">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-217">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-218">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-219">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-220">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-221">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-222">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="b1aea-223">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-224">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-225">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-226">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-227">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-228">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="b1aea-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="b1aea-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="b1aea-230">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-230">Member</span></span> | <span data-ttu-id="b1aea-231">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-232">Windows (platformy UWP)</span><span class="sxs-lookup"><span data-stu-id="b1aea-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="b1aea-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="b1aea-233">System.Net.Sockets</span></span>

| <span data-ttu-id="b1aea-234">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-234">Member</span></span> | <span data-ttu-id="b1aea-235">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-236">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-237">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="b1aea-238">System .NET. WebSockets</span><span class="sxs-lookup"><span data-stu-id="b1aea-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="b1aea-239">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-239">Member</span></span> | <span data-ttu-id="b1aea-240">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="b1aea-241">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="b1aea-242">System. odbicie</span><span class="sxs-lookup"><span data-stu-id="b1aea-242">System.Reflection</span></span>

| <span data-ttu-id="b1aea-243">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-243">Member</span></span> | <span data-ttu-id="b1aea-244">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-245">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-246">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-247">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-248">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-249">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-250">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="b1aea-251">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="b1aea-252">System.Runtime.CompilerServices</span><span class="sxs-lookup"><span data-stu-id="b1aea-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="b1aea-253">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-253">Member</span></span> | <span data-ttu-id="b1aea-254">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="b1aea-255">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="b1aea-256">System.Runtime.InteropServices</span><span class="sxs-lookup"><span data-stu-id="b1aea-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="b1aea-257">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-257">Member</span></span> | <span data-ttu-id="b1aea-258">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-259">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="b1aea-260">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-261">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-262">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-263">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-264">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-265">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="b1aea-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="b1aea-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="b1aea-267">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-267">Member</span></span> | <span data-ttu-id="b1aea-268">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="b1aea-269">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="b1aea-270">System. Security</span><span class="sxs-lookup"><span data-stu-id="b1aea-270">System.Security</span></span>

| <span data-ttu-id="b1aea-271">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-271">Member</span></span> | <span data-ttu-id="b1aea-272">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="b1aea-273">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="b1aea-274">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-275">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="b1aea-276">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="b1aea-277">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="b1aea-278">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="b1aea-279">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="b1aea-280">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="b1aea-281">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="b1aea-282">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="b1aea-283">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-284">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="b1aea-285">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="b1aea-286">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="b1aea-287">System. Security. Claims</span><span class="sxs-lookup"><span data-stu-id="b1aea-287">System.Security.Claims</span></span>

| <span data-ttu-id="b1aea-288">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-288">Member</span></span> | <span data-ttu-id="b1aea-289">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="b1aea-290">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-291">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-292">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-293">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-294">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="b1aea-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="b1aea-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="b1aea-296">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-296">Member</span></span> | <span data-ttu-id="b1aea-297">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-298">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-299">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="b1aea-300">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="b1aea-301">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="b1aea-302">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="b1aea-303">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="b1aea-304">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="b1aea-305">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="b1aea-306">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="b1aea-307">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="b1aea-308">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="b1aea-309">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="b1aea-310">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="b1aea-311">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b1aea-312">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="b1aea-313">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-314">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-315">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-316">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-317">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b1aea-318">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-319">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-320">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-321">Linux i macOS</span><span class="sxs-lookup"><span data-stu-id="b1aea-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-322">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-323">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="b1aea-324">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-325">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="b1aea-326">System. Security. Cryptography. PKCS</span><span class="sxs-lookup"><span data-stu-id="b1aea-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="b1aea-327">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-327">Member</span></span> | <span data-ttu-id="b1aea-328">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-329">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-330">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="b1aea-331">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="b1aea-332">System. Security. Cryptography. x509</span><span class="sxs-lookup"><span data-stu-id="b1aea-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="b1aea-333">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-333">Member</span></span> | <span data-ttu-id="b1aea-334">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-335">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-336">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-337">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-337">All</span></span> |
| <span data-ttu-id="b1aea-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (tylko ustaw)</span><span class="sxs-lookup"><span data-stu-id="b1aea-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="b1aea-339">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="b1aea-340">System. Security. Authentication. Kiedy</span><span class="sxs-lookup"><span data-stu-id="b1aea-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="b1aea-341">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-341">Member</span></span> | <span data-ttu-id="b1aea-342">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-343">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="b1aea-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="b1aea-344">System.Security.Policy</span></span>

| <span data-ttu-id="b1aea-345">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-345">Member</span></span> | <span data-ttu-id="b1aea-346">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-347">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="b1aea-348">System. ServiceProcess. ServiceController</span><span class="sxs-lookup"><span data-stu-id="b1aea-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="b1aea-349">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-349">Member</span></span> | <span data-ttu-id="b1aea-350">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-351">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="b1aea-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="b1aea-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="b1aea-353">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-353">Member</span></span> | <span data-ttu-id="b1aea-354">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-355">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="b1aea-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="b1aea-356">System.Threading</span></span>

| <span data-ttu-id="b1aea-357">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-357">Member</span></span> | <span data-ttu-id="b1aea-358">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-359">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-360">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="b1aea-361">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="b1aea-362">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="b1aea-363">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="b1aea-364">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="b1aea-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="b1aea-365">System.Xml</span></span>

| <span data-ttu-id="b1aea-366">Członek</span><span class="sxs-lookup"><span data-stu-id="b1aea-366">Member</span></span> | <span data-ttu-id="b1aea-367">Platformy, które generują</span><span class="sxs-lookup"><span data-stu-id="b1aea-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-368">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-369">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="b1aea-370">Wszyscy</span><span class="sxs-lookup"><span data-stu-id="b1aea-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="b1aea-371">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1aea-371">See also</span></span>

- [<span data-ttu-id="b1aea-372">Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="b1aea-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="b1aea-373">Serializacja binarna w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="b1aea-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="b1aea-374">Analizator przenośności platformy .NET</span><span class="sxs-lookup"><span data-stu-id="b1aea-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
