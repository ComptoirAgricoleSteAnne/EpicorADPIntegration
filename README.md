<p align="center">
  <img src="docs/banner.png" alt="Epicor ↔ ADP Integration Banner" width="600"/>
</p>

# ⚙️ Epicor ↔ ADP — Intégration des équipes de chantier

Ce projet fournit une **référence d’intégration** entre **Epicor** (Jobs/Opérations) et **ADP** (Shifts/Timesheets) afin d’automatiser la planification et le suivi des équipes de chantier.

---

## 🎯 Objectifs
- 🗂️ Générer automatiquement des **blocs de travail** à partir des jobs Epicor  
  *(1 bloc = 1 équipe × 1 journée × heures/jour)*.
- 📅 Publier ces blocs comme **shifts** dans ADP.
- 👷 Permettre au **répartiteur** d’assigner les employés aux blocs directement dans ADP.
- ⏱️ Récupérer les **heures pointées** et les **notes quotidiennes** validées par le chef d’équipe.
- ✅ Synchroniser les **heures réelles** dans Epicor (Job Labor) et clôturer la job avec validation par le superviseur.

---

## 🔄 Fonctionnement

1. **📌 Planification dans Epicor**  
   - Création d’une job (make-to-order) avec dates de début/fin, crew size et heures/jour.  
   - Export automatique vers ADP sous forme de blocs journaliers.  

2. **🧑‍💼 Assignation dans ADP**  
   - Le répartiteur affecte les employés aux shifts générés.  

3. **🛠️ Exécution & Validation**  
   - Les employés pointent leurs heures dans ADP.  
   - Le chef d’équipe valide quotidiennement les heures et ajoute les notes.  

4. **📤 Retour dans Epicor**  
   - Les heures et notes sont rapatriées dans la job Epicor.  
   - Le superviseur clôture la job dans Epicor et approuve les timesheets dans ADP.  


## 🗂️ Structure du repo
```text
epicor-adp-job-assignments/
├─ src/         # Worker .NET (polling Epicor ↔ ADP)
├─ docs/        # Documentation, mapping de champs, architecture
├─ schemas/     # JSON schemas des payloads
├─ infra/       # Dockerfile, manifests K8s, CI/CD
├─ samples/     # Exemples de payloads et Postman collection
└─ README.md    # Ce fichier
```

---

## 🛠️ Technologies
- 💻 .NET 8 Worker Service  
- 🔗 Epicor REST API  
- 🔗 ADP Workforce API  
- 🐳 Docker / ☸️ Kubernetes  
- 🤖 GitHub Actions (CI/CD)  

---

## 🚀 Démarrage rapide

1. **Cloner le projet**
   ```bash
   git clone https://github.com/<ton-org-ou-user>/epicor-adp-job-assignments.git
   cd epicor-adp-job-assignments


