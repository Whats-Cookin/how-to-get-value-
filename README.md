# how-to-get-value-

the idea of ProgressiveTrust is powerful, where they start with some self-signed credential, then they choose ways to enhance it, whether that is asking for a recommendation, signing in another way to link an account, or something else
10:50
that's why we try to have these decoupled claims, not one single process or schema, so people can add on later - and also, that we can connect to someone ELSE adding a claim maybe about their linkedin, even if they didn't ask them to
the signed verifiable credential right now can be just a LinkedClaim in our database, from which we can generate a proper VC

right now live.linkedtrust.us has the claims in a postgres database and the issuer and the proof just in database fields, not like vc blob

but yes

like ideally we have these fields, sign against a generated json, store the signature, can regenerate the valid VC, instead of having to have blobs all the time.  but that's a separate thing.

even if we store the whole blob we can also have the LinkedClaim fields to generate the nodes and edges, like the signed blob is essnetially the source of a LinkedClaim object

in our app this is the "Claim" table

i was hoping that the signed blob credentials would just be the source for "Claim" objects, but i thnk its not being coded that way, whatever thats fine

its ok to have different classes as long as they have subject, issuer, source would say when T3 sends credential, give the user a special link to it
1) user goes to link to see their credential in web of trust
2) user asks people to verify it or logs in in other ways
3) user gets display of credential in graph and in report
like the special link can be a proof they own that credential

 how do we know who sends the linkedclaim to us?
the user is logged in to linkedclaims.com and uses the api
It seems to me that claims issued by linkedclaims.com are MISSING the did of the SUBJECT
so for now, because they are all self-issued, we can use the issuer DID instead.
we do have the subjectName in the claim
(normally, the issuer of a claim is not the subject!  but in this case it is)
so the Subject of the claim is the person, with DID and Name
the Claim is "Skilled at UI/UX Design"
now, to know who it was sent us the claim, since they are not using their did to login to linkedtrust, we will have to give them a magic link
which is something you can do by generating a temporary token there are a lot of libraries to do this
now, to know who it was sent us the claim, since they are not using their DID to login to linkedtrust, we will have to give them a magic link

which is something you can do by generating a temporary token, there are a lot of libraries to do this


here’s a technical roadmap:

1️-DID-Based User Authentication
Allow users to register using a DID wallet (MetaMask, SpruceID, etc.).
Generate a DID for each user to serve as their decentralized identity.
2️- Strengthening Identity with Linked Accounts
Enable OAuth-based sign-in for LinkedIn & GitHub.
Generate "Same-As" Verifiable Credentials that link the DID to these accounts.
Store the VCs in a decentralized storage system (e.g., Ceramic Network, IPFS).
3️- Issuing & Storing Verifiable Credentials
The platform signs a VC that verifies Sahda’s LinkedIn & GitHub accounts.
Credentials are stored in her DID profile and shared when needed.
Use frontend Verifiable Credential standards for interoperability.
4️- Job Application Process
Instead of a resume upload, users share their signed credentials with employers.
Employers verify credentials on-chain without needing LinkedIn/GitHub API access.
5️- Employer Verification & Trust Mechanism
Employers validate credentials using a DID resolver.
Provide a dashboard showing applicants with verified trust levels.
